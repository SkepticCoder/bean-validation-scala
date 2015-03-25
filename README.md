# bean-validation-scala

JSR 303 and 349 Bean Validation for Scala.
This library enable validation to some Monad. (e.g. Option, Seq, etc)

[![Build Status](https://travis-ci.org/bean-validation-scala/bean-validation-scala.svg?branch=master)](https://travis-ci.org/bean-validation-scala/bean-validation-scala)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.tsukaby/bean-validation-scala_2.11/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.tsukaby/bean-validation-scala_2.11)
[![Scaladoc](http://javadoc-badge.appspot.com/com.tsukaby/bean-validation-scala_2.11.svg?label=scaladoc)](http://javadoc-badge.appspot.com/com.tsukaby/bean-validation-scala_2.11)

## Gitter Chat for Casual Q&A

- 英語 or 日本語 (English or Japanese): [![Join the chat at https://gitter.im/bean-validation-scala/bean-validation-scala](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/bean-validation-scala/bean-validation-scala?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Getting Started

    libraryDependencies ++= Seq(
      "com.tsukaby" %% "bean-validation-scala" % "0.4.0"
    )

This library has been published in the [Maven central](http://search.maven.org/#browse|999013097).

## How to use

Step 1. Add annotations to your case class.

    import javax.validation.constraints.Size

    case class Person(
      @(Size@field)(min = 4)
      name: Option[String]
    )

Step 2. Create validator by our library.

    import com.tsukaby.bean_validation_scala.ScalaValidatorFactory

    val validator = ScalaValidatorFactory.validator

Step 3. Validate a case class object.

      val obj = Person(Some("abc"))
      val violations = validator.validate(obj)

      if (violations.nonEmpty) {
        println("Violations found!")
      }

## Other information.

### Support annotations.

`javax.validation.constraints`

- AssertFalse
- AssertTrue
- DecimalMax
- DecimalMin
- Digits
- Future
- Max
- Min
- Past
- Pattern
- Size

`org.hibernate.validator.constraints`

- CreditCardNumber
- EAN
- Email
- Length
- LuhnCheck
- Mod10Check
- Mod11Check
- NotBlank
- NotEmpty
- Range
- SafeHtml
- URL

`com.tsukaby.bean_validation_scala`

Original annotations.

- AssertNone
- AssertSome
- ByteSize

### Doesn't support annotations.

- NotNull `// What do you think I should do?`
- Null
- ModCheck `// Deprecated`
- ParameterScriptAssert
- ScriptAssert


## Contribution

I'm seeking your PR!!!
I'm easy.

For example.

- Bug fix
- Refactoring the code.
- Add a new feature, new annotations and others.
- Fix my odd English texts.

## License

```
Copyright 2015 - 2015 tsukaby.com
MIT License
```
