# Writing Tests

If you haven't already, it's strongly recommended to read
the [introduction](../index) first, as it introduces the various test types.

There's also a load of [general guidelines](general-guidelines) that apply to all tests.

```eval_rst
.. toctree::
   :maxdepth: 1

   general-guidelines
   ahem
   assumptions
   css-metadata
   css-user-styles
   file-names
   h2tests
   lint-tool
   manual
   reftests
   rendering
   server-features
   submission-process
   testdriver
   testdriver-tutorial
   testharness
   visual
   wdspec
```

## Test Type

Tests in this project use a few different approaches to verify expected
behavior. The tests can be classified based on the way they express
expectations:

* Rendering tests should be used to verify that the browser graphically
  displays pages as expected. See the [rendering test guidelines][rendering]
  for tips on how to write great rendering tests. There are a few different
  ways to write rendering tests:

  * [Reftests](reftests) should be used to test rendering and layout. They
    consist of two or more pages with assertions as to whether they render
    identically or not.

  * [Visual tests](visual) should be used for checking rendering where there is
    a large number of conforming renderings such that reftests are impractical.
    They consist of a page that renders to final state at which point a
    screenshot can be taken and compared to an expected rendering for that user
    agent on that platform.

* [testharness.js](testharness) tests should be used (where possible!) for
  testing everything else. They are built with the testharness.js unit testing
  framework, and consist of assertions written in JavaScript.

* [wdspec](wdspec) tests are written in Python using
  [pytest](https://docs.pytest.org/en/latest/) and test [the WebDriver browser
  automation protocol](https://w3c.github.io/webdriver/)

* [Manual tests](manual) are used as a last resort for anything that can't be
  tested using any of the above. They consist of a page that needs manual
  interaction or verification of the final result.

In general, there is a strong preference towards reftests and testharness.js
tests types (as they can be easily run without human interaction), so they
should be used in preference to the others even if it results in a
somewhat cumbersome test; there is a far weaker preference between the
two test types, and it is at times advisable to use testharness.js tests
for things which would typically be tested using reftests but for
which it would be overly cumbersome.

See [file names](file-names) for test types and features determined by the file names,
and [server features](server-features) for advanced testing features.

## Submitting Tests

Once you've written tests, please submit them using
the [typical GitHub Pull Request workflow](submission-process); please
make sure you run the [`lint` script](lint-tool) before opening a pull request!
