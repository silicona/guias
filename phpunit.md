# phpunit

[Instalacion y primeros pasos](https://www.uno-de-piera.com/introduccion-a-las-pruebas-unitarias-con-phpunit/#)

Añadido archivo phpunit.xml.dist de configuracion de phpunit.

Ejemplos basicos

## Otro

[Instalacion y segundos pasos](http://www.baluart.net/articulo/introduccion-a-las-pruebas-unitarias-en-php-con-phpunit)

## Phpunit2

Aplicacion completa con TDD 

[mejor instalacion](https://blog.irontec.com/primeros-pasos-con-tdd-i/)

### Ejecuciones

Instalado con composer
  : `phpunit`
  : `phpunit --testsuite <nombre_suite>`
  : `phpunit <ruta/al/test>.php`
  : `phpunit <ruta/al/test>.php --filter <nombre_de_test>`

### Asserts

[Doc](https://phpunit.de/manual/6.5/en/appendixes.assertions.html)

Afirmaciones:
  : assertArrayHasKey()
  : assertClassHasAttribute()
  : assertArraySubset()
  : assertClassHasStaticAttribute()
  : assertContains()
  : assertContainsOnly()
  : assertContainsOnlyInstancesOf()
  : assertCount()
  : assertDirectoryExists()
  : assertDirectoryIsReadable()
  : assertDirectoryIsWritable()
  : assertEmpty()
  : assertEqualXMLStructure()
  : assertEquals()
  : assertFalse()
  : assertFileEquals()
  : assertFileExists()
  : assertFileIsReadable()
  : assertFileIsWritable()
  : assertGreaterThan()
  : assertGreaterThanOrEqual()
  : assertInfinite()
  : assertInstanceOf()
  : assertInternalType()
  : assertIsReadable()
  : assertIsWritable()
  : assertJsonFileEqualsJsonFile()
  : assertJsonStringEqualsJsonFile()
  : assertJsonStringEqualsJsonString()
  : assertLessThan()
  : assertLessThanOrEqual()
  : assertNan()
  : assertNull()
  : assertObjectHasAttribute()
  : assertRegExp()
  : assertStringMatchesFormat()
  : assertStringMatchesFormatFile()
  : assertSame()
  : assertStringEndsWith()
  : assertStringEqualsFile()
  : assertStringStartsWith()
  : assertThat()
  : assertTrue()
  : assertXmlFileEqualsXmlFile()
  : assertXmlStringEqualsXmlFile()
  : assertXmlStringEqualsXmlString()

### Anotaciones

[Doc](https://phpunit.de/manual/6.5/en/appendixes.annotations.html)

Anotaciones:
  : @author
  : @after
  : @afterClass
  : @backupGlobals
  : @backupStaticAttributes
  : @before
  : @beforeClass
  : @codeCoverageIgnore*
  : @covers
  : @coversDefaultClass
  : @coversNothing
  : @dataProvider
  : @depends
  : @doesNotPerformAssertions
  : @expectedException
  : @expectedExceptionCode
  : @expectedExceptionMessage
  : @expectedExceptionMessageRegExp
  : @group
  : @large
  : @medium
  : @preserveGlobalState
  : @requires
  : @runTestsInSeparateProcesses
  : @runInSeparateProcess
  : @small
  : @test
  : @testdox
  : @testWith
  : @ticket
  : @uses
