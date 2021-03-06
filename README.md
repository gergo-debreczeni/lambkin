Lambkin
=======
Lambkin is CLI tool for generating and managing simple in AWS Lambda.

Supporting Node.js and Python, Lambkin generates skeleton functions, provides
lightweight help for managing dependencies, and does its best to hide the
complexity of publishing and running functions in Lambda.

Quick Start
===========

Prerequisites
-------------
* A valid `~/.aws/config` file. eg.
```
[default]
region = us-west-2
```
* A valid `~/.aws/credentials` file. eg.
```
[default]
aws_access_key_id = AKIAUAVOHGHOOWEEYIED
aws_secret_access_key = 90kX2Y2bykTH9CpQFHCzN92tukYf26
```

* A working `virtualenv` command if you will be writing Lambda functions in Python.

Installing
----------
* `pip install lambkin`

Examples
--------

##### Create a new Python function from a basic template

``` bash
lambkin create cool-func
cd cool-func
$EDITOR cool-func.py
```

##### ...or a maybe you prefer Node.js

``` bash
lambkin create cool-func --runtime=nodejs
cd cool-func
$EDITOR cool-func.js
```

##### Install packages and dependencies for a Python function

``` bash
$EDITOR requirements.txt
lambkin build
```

##### Install packages and dependencies for a Node.js function

``` bash
$EDITOR Makefile
lambkin build
```

##### Bundle up your function (with libraries) and send it to Lambda

``` bash
lambkin publish --description 'The best function ever.'
```

##### Increase the timeout for a long-running function

``` bash
lambkin publish --description 'Slow' --timeout=300
```

##### Invoke the published function, right now!

``` bash
lambkin run
```

##### Schedule the function to run at regular intervals

``` bash
lambkin schedule --rate='10 minutes'
```

##### Remove the function from Lambda, but keep it locally

``` bash
lambkin unpublish
```

Dependencies - pip and npm
--------------------------
Python functions get a `requirements.txt` file where you can specify
dependencies. They will be installed into your function's virtualenv by
`lambkin build`.

For now, Node.js functions just get a Makefile. Nicer, more Node-ish
dependency management is planned for the future.
