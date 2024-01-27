# Visualization Workbook

Some examples.

First try with Python 3.12 failed due to incompatible version of `mpld3`. Python 3.11 worked fine:

Use `matplotlib.pyplot` instead of `PyLab`. Read [here](https://matplotlib.org/stable/api/pylab.html#module-pylab).

Pyhton `venv`:

```
...311/python -m venv .venv
source .venv/Scripts/activate
python -m pip install -r requirements.txt
```


Simple instructions [here](https://www.linkedin.com/pulse/enhance-your-powerpoint-presentations-animated-figures-grega-smrkolj/) for getting the HTML interactive things in a ppt. Key pieces are:
1. enabling the Web Viewer add-in in ppt
2. putting the content on a public site. GitHub is easiest, as it is easy to upload and easy to serve content in different ways.


Easiest way to get the plot online: upload to GH, select raw, replace `githubusercontent` with `githack` in URL. [Example](https://raw.githack.com/rlanzafame/visualizations/main/html_examples/top_bottom_bed.html)

When using these visualizations something starts OpenJDK (open source Java, not JavaScript...not sure why), which eats up tons of memory. Hmmmm...