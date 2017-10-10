# Python

## Decorators

_Decorators_ añadidos desde Python 2.4 para permitir que el _function
and method wrapping_ fuese más fácil de leer y entender.  _function
and method wrapping_ consiste en implementar una función (o método)
que recibe como parámetro una función (¿o método?) y devuelve una
función mejorada.

El caso de uso original era definir los métodos como métodos de Clase
o métodos estáticos en la cabecera de su definición.

La receta general:

~~~~{python}
def mydecorator(function):
    def _mydecorator(*args, **kw):
        # do some stuff before the real 
        # function gets called 
        res = function(*args, **kw)
        # do some stuff after
        return res
    # returns the sub-function
    return _mydecorator
~~~~

El intérprete carga los _decorators_ cuando se lee el módulo la
primera vez, debe limitarse su uso a _wrappers_ que puedan aplicarse
de forma genérica. Si el _decorator_ está fuertemente acoplado con la
clase o función que decora debería reescribirse y convertirlo en un
invocable regular para evitar la complejidad.

Patrónes típicos:

* Argument checking
* Caching
* Proxy
* Context provider

___ 
> __Nota:__ En web2py parece que los _decorators_ se usan
> tipicamente como proveedores de contexto. Hay que ver como funciona la
> sentencia `with` de Python 2.5 que se crea con el mismo propósito.


