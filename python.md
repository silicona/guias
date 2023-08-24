# Python 3.6.5

[Documentacion](https://docs.python.org/3.6/index.html)

[Tutorial](https://docs.python.org/3.6/tutorial/index.html)



Instalacion desde ejecutable desde web de Python

## Ejecucion
Utiliza `py flags nombre_archivo` para ejecutar scripts en consola
  : Version - `py --version`
  : Help - `py -h`

### Archivos

#### Windows

Instalacion tipica en directorio tipo 'users/Oclem1/appdata/local/programs/python/python36-32/'.
Libreria de modulos en 'lib/'.

## Django
[Docs](https://docs.djangoproject.com/en/4.1/intro/tutorial02/)

### Shell
- Ejecutar : `python3 manage.py shell`

### Conexion BBDD
Establecido en project/project/settings.py

- Backend Mysql - Mac:
  - Instalar mysql con brew
  - Exportar path de mysql: `export PATH=$PATH:/usr/local/mysql/bin`
  - Instalar mysqlclient: `pip3 install mysqlclient`

Comandos:
- Migración del proyecto de todas las apps registradas: `python3 manage.py migrate`
- Migración de app del proyecto: 
  - Añadir la app a settings.py:INSTALLED_APPS
  - Ejecutar para crear migracion en carpeta de app/migrations: `python3 manage.py makemigrations app`
  - Ejecutar para ver el sql de la migración: `python3 manage.py sqlmigrate app 0001`

#### Database for model
[src](https://stackoverflow.com/questions/3519143/django-how-to-specify-a-database-for-a-model)
- DbRouter example:
  ```
  # app/dbrouters.py
  from app.models import SomeModel
  class MyDBRouter(object):

      def db_for_read(self, model, **hints):
          """ reading SomeModel from otherdb """
          if model == SomeModel:
              return 'otherdb'
          return None

      def db_for_write(self, model, **hints):
          """ writing SomeModel to otherdb """
          if model == SomeModel:
              return 'otherdb'
          return None
  # app/settings.py
  DATABASE_ROUTERS = ('app.dbrouters.MyDBRouter',)
  DATABASES = {
      ...
      'otherdb': {
          ....
      }
  }
  ```
- Model owner (por comprobar):
  ```
  class User(models.Model):
    birth_date = models.DateField()

    class Meta:
        managed = False
        db_table = 'myotherapp_user'

  User.objects = User.objects.using('myotherdb')
  ```

## Libreria Requests

[Documentacion de docs.Python](http://docs.python-requests.org/es/latest/user/quickstart.html#realizar-un-peticion)


## TDD

[Unitest Docs](https://docs.python.org/3/library/unittest.html)

[Docs stable](https://python.readthedocs.io/en/stable/library/unittest.html)

[Asserts](https://docs.python.org/3/library/unittest.html#classes-and-functions)

|                      Method                      |                            Checks that                            | New in |
| :----------------------------------------------: | :---------------------------------------------------------------: | :----: |
|                assertEqual(a, b)                 |                              a == b                               |        |
|               assertNotEqual(a, b)               |                              a != b                               |        |
|                  assertTrue(x)                   |                          bool(x) is True                          |        |
|                  assertFalse(x)                  |                         bool(x) is False                          |        |
|                  assertIs(a, b)                  |                              a is b                               |  3.1   |
|                assertIsNot(a, b)                 |                            a is not b                             |  3.1   |
|                 assertIsNone(x)                  |                             x is None                             |  3.1   |
|                assertIsNotNone(x)                |                           x is not None                           |  3.1   |
|                  assertIn(a, b)                  |                              a in b                               |  3.1   |
|                assertNotIn(a, b)                 |                            a not in b                             |  3.1   |
|              assertIsInstance(a, b)              |                         isinstance(a, b)                          |  3.2   |
|            assertNotIsInstance(a, b)             |                       not isinstance(a, b)                        |  3.2   |
|     assertRaises(exc, fun, \*args, \*\*kwds)     |                 fun(\*args, \*\*kwds) raises exc                  |        |
| assertRaisesRegex(exc, r, fun, \*args, \*\*kwds) | fun(\*args, \*\*kwds) raises exc and the message matches regex r  |  3.1   |
|     assertWarns(warn, fun, \*args, \*\*kwds)     |                 fun(\*args, \*\*kwds) raises warn                 |  3.2   |
| assertWarnsRegex(warn, r, fun, \*args, \*\*kwds) | fun(\*args, \*\*kwds) raises warn and the message matches regex r |  3.2   |
|            assertLogs(logger, level)             |         The with block logs on logger with minimum level          |  3.4   |
|             assertAlmostEqual(a, b)              |                        round(a-b, 7) == 0                         |        |
|            assertNotAlmostEqual(a, b)            |                        round(a-b, 7) != 0                         |        |
|               assertGreater(a, b)                |                               a > b                               |  2.7   |
|             assertGreaterEqual(a, b)             |                              a >= b                               |  2.7   |
|                 assertLess(a, b)                 |                               a < b                               |  2.7   |
|              assertLessEqual(a, b)               |                              a <= b                               |  2.7   |
|            assertRegexpMatches(s, r)             |                            r.search(s)                            |  2.7   |
|           assertNotRegexpMatches(s, r)           |                          not r.search(s)                          |  2.7   |
|              assertItemsEqual(a, b)              |       sorted(a) == sorted(b) and works with unhashable objs       |  2.7   |
|          assertDictContainsSubset(a, b)          |              all the key/value pairs in a exist in b              |  2.7   |
|            assertMultiLineEqual(a, b)            |                              strings                              |  3.1   |
|            assertSequenceEqual(a, b)             |                             sequences                             |  3.1   |
|              assertListEqual(a, b)               |                               lists                               |  3.1   |
|              assertTupleEqual(a, b)              |                              tuples                               |  3.1   |
|               assertSetEqual(a, b)               |                        sets or frozensets                         |  3.1   |
|              assertDictEqual(a, b)               |                               dicts                               |  3.1   |


`unittest.TestResult`

[Gran curso Python3](http://www.diveintopython3.net/table-of-contents.html#your-first-python-program)


### PYGRAPHVIZ

[Docs](https://pygraphviz.github.io/documentation.html)

[Docs Graphviz](https://graphviz.org/doc/info/shapes.html)



