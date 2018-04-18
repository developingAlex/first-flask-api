# Simple python flask API

## Install flask

Use a virtual environment for the app so that it can maintain its own libraries
without worrying about versions.

### Prerequisites

* `sudo apt install python3-venv`

### Walkthrough

1. Make a new virtual environment in a directory called flask-env:<br>
    `python3 -m venv flask-env`

1. Activate the environment:<br>
    `chmod u+x flask-env/bin/activate`<br>
    `source flask-env/bin/activate`
1. `pip install Flask`
    * This gave a red warning output: <br>`Failed building wheel for MarkupSafe`
    * This gave a warning output: <br>`You are using pip version 8.1.1, however version 10.0.0 is available.`<br>`You should consider upgrading via the 'pip install --upgrade pip' command.`
1. `pip install --upgrade pip`
1. Wasting a lot of time trying to investigate this Failed building wheel for 
MarkupSafe issue.. the main parts of the error output are:<br>
`Running setup.py bdist_wheel for itsdangerous ... error`<br>
&vellip;<br>
`error: invalid command 'bdist_wheel'`<br>
&vellip;<br>
`Failed building wheel for itsdangerous`<br>
&vellip;<br>
`Running setup.py bdist_wheel for MarkupSafe ... error`<br>
&vellip;<br>
`error: invalid command 'bdist_wheel'`<br>
&vellip;<br>
`Failed building wheel for MarkupSafe`

    Looks like a 
    [possible solution](https://stackoverflow.com/questions/34819221/why-is-python-setup-py-saying-invalid-command-bdist-wheel-on-travis-ci) 
    is to just run:<br>
    `pip install wheel`

    Now running:<br>
    `pip uninstall Flask`<br>
    `pip install Flask`<br>

    But that seemed to complete way too quickly, as if it didn&rsquo;t retry all the 
    things it did the first time.

    going to try doing the same for the packages that produced the errors 
    originally:<br>

    `pip uninstall Flask`<br>
    `pip uninstall itsdangerous`<br>
    `pip uninstall MarkupSafe`<br>
    `pip install MarkupSafe`<br>
    `pip install itsdangerous`<br>
    `pip install Flask`<br>

    Ok going to assume that is sorted out now and continue on&hellip;

1. 