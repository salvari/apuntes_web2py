# Tutoriales en la red

## Killer Web Development por Marco Laspe

Disponible [aquí](http://killer-web-development.com)

### Cambios

`Crud` debe ser importado explícitamente:

~~~~{python}
from gluon.tools import Crud
crud = Crud(db)
~~~~

Despues ya podemos seguir el tutorial haciendo por ejemplo:

~~~~{python}
def entry_post():
    """returns a form where the user can entry a post"""
    form = crud.create(db.post)
    return dict(form=form)
~~~~

