# Ruby


## Selenium

[ejemplos](https://gist.github.com/kenrett/7553278)

[The main website](https://cucumber.io/)
[Documentation](https://docs.cucumber.io)
[Ruby API Documentation](http://www.rubydoc.info/github/cucumber/cucumber-ruby/)

[Backgrounder](https://github.com/cucumber/cucumber/wiki/Cucumber-Backgrounder)

### Capybara

[cheatsheet](https://github.com/rstacruz/cheatsheets/blob/master/capybara.md)


## Pg

[Instalar solo gema](https://michaelrigart.be/install-pg-ruby-gem-without-postgresql/)
Libpq - Libreria de funciones interfaz para la bbdd

  - Ejecutar `brew install libpq`
  - Instala libpq en `usr/local/opt/libpq`
  - If you need to have libpq first in your PATH run: `echo 'export PATH="/usr/local/opt/libpq/bin:$PATH"' >> ~/.bash_profile`

### Instalacion Mac
- `gem uninstall pg`
- Opcion con Brew: `brew install postgresql@14`
- Ejecutar `gem install pg -- --with-opt-dir="/usr/local/opt/libpq"`

- Con bundle:
  - `bundle config --local build.pg --with-opt-dir="/usr/local/opt/libpq"`
  - `bundle install`

## RVM

[Docs](https://rvm.io/)

Instalar version de ruby
    Ejecutar `rvm install ruby-X.X.X`

Usar una version en conreto
    Ejecutar `rvm --default use ruby-X.X.X`