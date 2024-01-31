# Visualization Workbook

Some examples.

## Bed example

_How to get a Plotly-generated interactive figure (HTML) into a ppt?_

Simple instructions [here](https://www.linkedin.com/pulse/enhance-your-powerpoint-presentations-animated-figures-grega-smrkolj/) for getting the HTML interactive things in a ppt. Key pieces are:
1. enabling the Web Viewer add-in in ppt
2. putting the content on a public site. GitHub is easiest, as it is easy to upload and easy to serve content in different ways.

Easiest way to get the plot online: upload to GH, select raw, replace `githubusercontent` with `githack` in URL. [Example here](https://raw.githack.com/rlanzafame/visualizations/main/html_examples/top_bottom_bed.html). This is the link that goes into the Web Viewer add-in on ppt.

When using these visualizations something starts OpenJDK (open source Java, not JavaScript...not sure why), which eats up tons of memory. Hmmmm...

## Environment

First try with Python 3.12 failed due to incompatible version of `mpld3`. Python 3.11 worked fine:

Use `matplotlib.pyplot` instead of `PyLab`. Read [here](https://matplotlib.org/stable/api/pylab.html#module-pylab).

Python `venv`:

```
../../python_source/311/python -m venv .venv
...311/python -m venv .venv
```

```
source .venv/Scripts/activate
```

```deactivate```

```rm -r .venv```

```
python -m pip install -r requirements.txt
```

added twisted but it might not have worked

## Local Secure Host (SSL)

ppt needs a secure connection (HTTPS/SSL).

## SSL cert

Started [here](https://docs.twisted.org/en/stable/core/howto/tutorial/factory.html#introduction) and got certificates set up. Needed a byte conversion to work (commit `2f3af4c`). Found higher level page [here](https://docs.twisted.org/en/stable/core/howto/ssl.html) later...start on that one if revisiting this issue.


Create a certificate:
```
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
```

followed by username/password: `test/test`, then `NL` and `.` (blank) for the rest.

Recreated environment (note that `pyopenssl` is the PyPI namespace for OpenSSL). Still a lot of dependency issues:
- some packages had conflicts from `requirements.txt` setup (but some version was still there)
- had to install things like `zope`, `twisted`
- had to install `pyopenssl` _again_
- Also needed `python -Im pip install service-identity`

added these to `requirements.txt` but did not test with new one.

Finally `python -m finger22` ran completely, but then terminal freezes, or does not show output. Not sure how (or if) a web server was actually created.

Final attempt was to take the code from [here](https://stackoverflow.com/questions/19705785/python-3-simple-https-server) and put it in `test.py`, which didn't work (as default), nor by changing port (commit `371bf67`). Still froze terminal and no site at https. Oh well...