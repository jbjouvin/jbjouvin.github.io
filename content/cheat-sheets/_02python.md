+++ 
date = "1979-01-01"
title = "python"
description = "Some Python links"
slug = "fab fa-python"
type = "dev"
+++

<h2 id=Python>Python
<img src="https://www.python.org/static/opengraph-icon-200x200.png" height="100" width="100" align="right">

</h2>

* os

```py
import os
pythonpath = os.envrion["PYTHONPATH"]
```

```py
def save_game(self):
    """
    un fichier .sav est créé a chaque mouvement
    """
    chemin = os.path.join("cartes", self.nom + "sav")
    with open(chemin, 'w') as fichier:
        fichier.write(self.labystr)
    if self.position[3] == 'U':
        os.remove(chemin)
```


* math
* random
* shutil
* pickle
* sqlite3
* csv
* json
* logging
* base64
* venv
* timeit
* time

```py
# Find execution time:
import time
start = time.time()
"the code you want to test stays here"
end = time.time()
print(end - start)
```

* unittest

