# Groovy

- dynamic language
- compiles to JVM bytecode
- brings advanced concepts to the JVM
- mature IDE support

## Static languages:

- static languages enforce typing constraints at compile time - many bugs are caught early in development - yields performance gains - can introduce friction in development - ill-suited to working with flexible data formats

## Dynamic languages:

- dynamic languages enforce typing constraints at runtime - can lead to more rapid development - well-suited to working with flexible data formats - some bugs may not be found until later in development - performance tends to be slower

## Strongly typed:

- Strongly typed languages will not allow inappropriate operations on an object

- Weakly typed languages will allo any operation on any object

## The Polyglot Programmer

statig languages (Java, Scala) -> Dynamic Languages (Groovy, Clojure, JRuby)
-> DSLs (Apache, Camel, Gradle)

1. DSL - domain specific langugage
2. GPL - general purpose langugage
3. DSLs are often build on GPL

Grails allows you to build web servers written entirely in Groovy,
so groovy can be used no only Polyglot Application.
Griffon allows you to build desktop applications written entirely in Groovy.

## Why Groovy:

- is very accessible to Java developers
- can use existing Java libraries
- groovy extends java.lang.Object
- web application development
- building DSLs
- written acceptance tests
- scripting in a JVM environment

GVM - groovy environment manager

Basic syntax:

System.out.println("hello"); //print smth
println "hello" // semicolon is optional

Collections:

```groovy
def beatles = ["John", "Paul", "George"]
for (int i = 0; i < beatles.size(); i++){
println "Hello " + beatles[i]
}

for (int i = 0; i < beatles.size(); i++){
def greeting = "Hello "
println "\$greeting" + beatles[i]
}

for (int i = 0; i < beatles.size(); i++){
def greeting = "Hello "
println "$greeting" + "${beatles[i]}"
println "\${1\*10}"
}

for (beatle in beatles) {
println "\$beatle"
}

```

## Ranges:

```groovy
def numbers = 1..10
for (num in numbers){
println num
}

def range = 'a'..'g'

def enum DAYS {
SUN,
MON
}

def weekdays = DAYS.SUN..DAYS.MON
```

## Functions:

```groovy
def isEven(def num){
return num%2 == 0
}

def isEven(num){
num%2 == 0 //return implicit
}
```

## Closures:

def myClosure = { println "In a closure" }
myClosure()

//////

```groovy
def myClosure = {
println "In a closure"
println new Date()
}
for(i in 1..3){
myClosure()
sleep(1000)
}

///////
(1..3).each({
println "in a closure \$it"
})

///////
(1..3).each({ i ->
println "in a closure \$i"
})

(1..10).findAll({ return it%2==0 }).each({
println "in a closure: \$it"
})

```

## Dynamic capabilities:

duck typing - looks like duck and bahave like duck, it is duck

```groovy
def cat = "meow"
def one = 1

println cat
println cat.getClass()
println cat.toUpperCase()

println one
println one.getClass()

```

## XML:

GPX:

- an XML format for exchange GPS data
- open format
- widely supported in the industry

Reading XML:

- DOMCategory - lov-level access to Java`s DOM API
- XmlParser
  - eager evaluation
- XmlSlurper
  - lazy evalutation

example:

```groovy
def file = new File('loop.gpx')
println file.exists()

def slurper = new XmlSlurper()
def gpx = slurper.parse(file)
println gpx.name
println gpx.desc
println gpx.@version

for(point in gpx.rte.rtept){
println point.@lat
}

```

Writing XML:

- MarkupBuilder - simple XML creation
- StreamingMarkupBuilder - advanced XML creation - better support for large documents

example:

```groovy
def inFile = new File('loop.pgx')
def slurper = new XmlSlurper()
def gpx = slurper.parse(inFile)

def markupBuilder = new groovy.xml.StreamingMarkupBuilder()
def xml = markupBuilder.bind{
route {
mkp.comment(gpx.name)
gpx.rte.rtept.each{point ->
routepoint(timestamp: point.time.toString()) {
laitude(point.@lt)
longitude(point.@lan)
}
}
}
}

def outFile = new File('loop_updated.xml')
outFile.write(xml.toString())

```

## Calling Java from Groovy:

Grape:

- dependency management for Groovy
- natively supported in the Groovy language
- built on Ivy

Ivy

- Maven Repository-compatible dependency management
- Uses Maven coordinates for dependency resolution
- Automatically installs these dependencies at runtime

## Unit testing in Groovy:

Good Unit test:

- fast
- isolated
- repeatable
- self-verifying
- timely
  (first)

Red-Green-Refactor

- watch the test fail
- write just enough code for the test to pass
- refactor the code

Benefits of TDD

- results in clean APIs
- testable code is flexible code
- results in much less production code
- no need to schedule 'unit-testing' time
  Disadvantages:
- increases initial development time
- has a significant learning curve
- difficult without full team buy-in

Unit testing support in groovy:

- JUnit is built directrly into the groovy runtime
- mocking APIs are included int the groovy platform
- advanced testing frameworks are also available

Example:

creates automatically getters and setters

````groovy
class BankAccount{
private balance

    BankAccount(openingBalance){
    	balance = openingBalance
    }

    def void deposit(amount) {
    	balance += amount
    }

    def void withdraw(amount){
    	if(amount > balance)
    		throw new Exception()

    	balance -= amount
    }

    def getBalance(){
    	return balance
    }

}

## ```

```groovy
import groovy.util.GroovyTestCase

class BankAccountTests extends GroovyTestCase {

    def void setUp(){
    	println 'in setup'
    }

    def void tearDown(){
    	println 'in teardown'
    }

    def void testCanDepositMoney(){
    	def account = new BankAccount(10)
    	account.deposit(5)
    	assert 15 == account.balance
    }

    def void testCanWithdrawMoney(){
    	def account = new BankAccount(25)
    	account.withdraw(5)
    	assert 20 == account.balance
    }

}

## ```

improvement:

```groovy
import groovy.util.GroovyTestCase

class BankAccountTests extends GroovyTestCase {

    private account

    def void setUp(){
    	account = new BankAccount(10)
    }

    def void tearDown(){
    	account = null
    }

    def void testCanDepositMoney(){
    	account.deposit(5)
    	assert 15 == account.balance
    }

    def void testCanWithdrawMoney(){
    	account.withdraw(5)
    	assert 5 == account.balance
    }

    def void testCanNoWithdrawMoreMoneyThanBalance(){
    	shouldFail {
    		account.withdraw(15)
    	}
    }

}

````

## Mock object:

- a simulated object that immics the behavior of a real object in a controlled way.

## Stubs:

- can be used as stand-in objects
- will return canned values when asked

## Mocks:

- supports all the functionality of stubs
- can verify a member was called a certain number of times
- can assert a specific interaction occurred

example:

```groovy
class BankAccount{
private balance

    BankAccount(openingBalance){
    	balance = openingBalance
    }

    def void deposit(amount) {
    	balance += amount
    }

    def void withdraw(amount){
    	if(amount > balance)
    		throw new Exception()

    	balance -= amount
    }

    def getBalance(){
    	return balance
    }

    def void accrueInterest(){
    	def service = new InterestRateService()
    	def rate = service.getInterestRate()

    	def accruedInterest = balance * rate

    	deposit(accruedInterest)
    }

}

class InterestRateService {
def double getInterestRate(){
return 0.0
}
}

import groovy.util.GroovyTestCase
import groovy.mock.interceptor.\*

class BankAccountTests extends GroovyTestCase {

    private account

    def void setUp(){
    	account = new BankAccount(10)
    }

    def void tearDown(){
    	account = null
    }

    def void testCanDepositMoney(){
    	account.deposit(5)
    	assert 15 == account.balance
    }

    def void testCanWithdrawMoney(){
    	account.withdraw(5)
    	assert 5 == account.balance
    }

    def void testCanNoWithdrawMoreMoneyThanBalance(){
    	shouldFail {
    		account.withdraw(15)
    	}
    }

    // def void testCanAccrueInterest(){
    // 	def service = new StubFor(InterestRateService)
    // 	service.demand.getInterestRate {
    // 		return 0.10
    // 	}
    // 	service.use {
    // 		account.accrueInterest()

    // 		assert 11 == account.balance
    // 	}
    // }

    def void testCanAccrueInterest(){
    	def service = new MockFor(InterestRateService)
    	service.demand.getInterestRate {
    		return 0.10
    	}
    	service.use {
    		account.accrueInterest()

    		assert 11 == account.balance
    	}
    }


}
```

/////////////////

## Digging deeper with groovy syntax:

groovy extension method:

```groovy
println 'Beginning dump....'
println gpx.name.value.dump()

println 'Beginning inspect...'
println gpx.name.inspect() //must be manualy implemented

//with method can be run with all objects and closures
gpx.with {
println name
println ''
}
//ampersand syntax is uncompatible with with method, fot that
// is another syntax

gpx.with {
println attributes()['version']
}
println gpx.@version
```

groovy truthfulness:

## groovysh - groovy shell

examples:
assert 1 == 2 //false
assert 1 == 1 // true but nothing show
assert null == false // false
assert !null == false // false but null is truthy now
assert !!null == false // true

if (time == null) <-> if(!time)

## Adding Functionality with Categories:

use(DateTimeCategory){ //use method get category of class, specify inside context
// closures
}
Summary:

- extension methods are available on native objects
- groovy`s truth model allows for more succinct null checks
- categories allow you to easily add custom logic to existing classes

///////////////

## Working with REST Services:

///////////////

## Working with Databases Using Groovy:
