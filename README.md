brythonmagic
============

Brython magic for the IPython notebook.

The brythonmagic extension has been tested on:

* IPython versions (2, 0, 0, ''), (1, 2, 1, ''), (1, 2, 0, '') and (1, 1, 0, '')

* Python version 3.3.1

* Brython version [2,0,0,'final',2]

Installation
============

Just type the following:

```python
%install_ext https://raw.github.com/kikocorreoso/brythonmagic/master/brythonmagic.py
```    

```python
%load_ext brythonmagic
```

And load the brython js lib in the notebook:

```python
%%HTML
<script type="text/javascript" src="http://brython.info/src/brython_dist.js"></script>
```

Usage
=====

The brythonmagic provides you a cell magic, `%%brython`, to run brython code and show the results in a html `div` tag below the code cell. Best way to start with Brython is to check [the Brython docs in their home page](http://brython.info/doc/en/index.html).

example:

```python
%%brython -c zone
# First of all, the import of some libraries
from browser import doc, html

# All the elements will be inserted in the div with the "zone" id
zone = doc['zone']

# We create a new div element
newdiv = html.DIV(Id = "new-div")
# Now we add some style
newdiv.style = {"padding": "5px", 
           "backgroundColor": "#ADD8E6"}

# We create a new link and add the link to a string
blink = html.A('brython',href="http://brython.info")
text = "Brython is really cool, look at "+ blink+ " for more"

# Now we add the text to the div with id="new-div"
# the line below is equivalent to newdiv <= html.DIV(text,"banner")
newdiv.append(html.DIV(text,"banner"))

# Finally, we add the newdiv to the outer div with id="zone"
# zone <= newdiv is equivalent to zone.append(newdiv)
zone <= newdiv
```    

You can use several options:

* -p, --print: will show you the generated html code below the results obtained from the brython code.


* -c, --container: you can define the name of the `div` container in case you want to 'play' with it in other cell. If you don't define an output the `div` will have and `id` with the following format 'brython-container-[random number between 0 and 999999]'


* -i, --input: you can pass variables defined in the Python namespace separated by commas. If you pass a python list it will be converted to a brython list, a python tuple will be converted to a brython tuple, a python dict will be converted to a brython dict, a python string will be converted to a brython string.


* -h, --html: you can pass a string with html markup code. This html code will be inserted inside the div container. In this way you can avoid the generation of HTML markup code via a Brython script so you can separate the layout from the 'action'.


* -s, --script: Use this option to provide and id to the script defined in the Brython code cell. Also, this value could be used to run the code of this cell in other brython cells.


* -S, --scripts: Use this option to run code previously defined in other Brython code cells. The values should be the provided values in the -s/--script option in other Brython code cells.


[WARNING] This options may change as the brythonmagic is in active development. 

To see some examples download the notebook available in the repository and run it locally or see it in the [nbviewer](http://nbviewer.ipython.org/urls/raw.githubusercontent.com/kikocorreoso/brythonmagic/master/notebooks/Brython%20usage%20in%20the%20IPython%20notebook.ipynb?create=1) (you will loose the interactivity if you choose the second option). Also, you can take a look on the following video: http://youtu.be/adQzjuUX0kw

Support
=======

If you need Brython support, please, ask here: https://groups.google.com/forum/?fromgroups=#!forum/brython

If you need IPython support, please, ask here: http://mail.scipy.org/mailman/listinfo/ipython-dev

If you find a bug or want to propose a new feature open a new issue here: https://github.com/kikocorreoso/brythonmagic/issues

If you want to improve the code, fork, commit and PR ;·D

IDEAS
=====

Add an option to include *.py scripts? These *.py scripts should be Brython compatible.

Add an option to include a HTML structure so you don't have to create the structure via Brython code? &#10004;

Add an option to run more than one Brython script in a code cell? Right now, if you run a Brython code cell, the code in other cells will not work anymore (i.e., \_\_BRYTHON\_\_.vars.\_\_main\_\_ will be overwritten). &#10004; 
