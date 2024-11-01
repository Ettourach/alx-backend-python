#Unittests and Integration Tests

#what is unittests/integration

1.Unit testing is the process of testing that a particular function returns expected results for different set of inputs. A unit test is supposed to test standard inputs and corner cases. A unit test should only test the logic defined inside the tested function. Most calls to additional functions should be mocked, especially if they make network or database calls.

The goal of a unit test is to answer the question: if everything defined outside this function works as expected, does this function work as expected?

2.Integration tests aim to test a code path end-to-end. In general, only low level functions that make external calls such as HTTP requests, file I/O, database I/O, etc. are mocked.

Integration tests will test interactions between every part of your code.

3.We will using it to executing ours tests

"$ python -m unittest path/to/test_file.py"

#The difference between unit and integration tests.

the main difference between unit tests and integration tests lies in what they test and how isolated or integrated the parts of the application are during testing.

1. Unit Tests
Purpose: Unit tests focus on individual components or functions in isolation. Their goal is to verify that each piece of code works as expected by itself.
Scope: They test small parts of the application, usually a single function or class.
Environment: Typically run in a controlled environment where dependencies are mocked or stubbed, so no external resources (like databases or APIs) are used.
Speed: They are generally very fast because they don't rely on external systems.
Example: Testing a function that calculates the sum of two numbers, independent of the rest of the codebase.
2. Integration Tests
Purpose: Integration tests check how different modules or components work together. They ensure that individual parts integrate correctly to perform complex operations.
Scope: These tests cover multiple components, often involving dependencies like databases, APIs, or other parts of the system.
Environment: They are run in a more complete environment where actual dependencies may be used, so they can test real interactions.
Speed: Integration tests are usually slower than unit tests because they involve more components and may rely on real services.
Example: Testing a function that fetches data from an API, processes it, and saves it to a database.
In summary:

Unit tests = Isolated, small components, fast, test in isolation.
Integration tests = Combined components, real dependencies, slower, test how parts work together.

#Common testing patterns such as mocking, parametrizations and fixtures

Here’s an overview of some common testing patterns that make tests more effective and manageable:

1. Mocking
Purpose: Mocking is used to simulate the behavior of external systems or dependencies (like databases, APIs, or other functions) to isolate the code being tested.
When to Use: It’s ideal when testing code that relies on external resources, network calls, or any state that would make the test unpredictable or slower.
Implementation: You replace the actual dependencies with “mock” objects that mimic the behavior of the real ones, often returning predefined results.
Example: Mocking a database call in a function to return a fixed result instead of actually querying a database.
2. Parametrization
Purpose: Parametrization is the practice of running the same test with multiple sets of inputs to cover a wider range of cases efficiently.
When to Use: This is useful when you want to verify that a function behaves correctly with various inputs without writing separate tests for each case.
Implementation: In testing frameworks like pytest, you can use @pytest.mark.parametrize to specify different input and output combinations for a single test.
Example: Testing a “sum” function with different pairs of numbers to check if it consistently returns the correct result.
3. Fixtures
Purpose: Fixtures set up a known state or environment for tests, ensuring consistency by providing the necessary context or setup before tests run.
When to Use: Useful when tests require specific configurations, resources, or data to run, such as database connections or temporary files.
Implementation: Fixtures are typically defined in testing frameworks (like @pytest.fixture in pytest) and are automatically made available to any test that needs them.
Example: Creating a temporary database or initializing a set of objects that multiple tests depend on, then cleaning up after the test finishes.
Putting It All Together
These patterns can often be combined for even more robust testing:

Mocking with fixtures: You can mock dependencies and use a fixture to set them up consistently across tests.
Parametrization with fixtures: Run a parametrized test using data from a fixture to verify the function with multiple scenarios set up by the fixture.
These patterns help make tests more flexible, reusable, and efficient, allowing for faster development and more comprehensive coverage.

#end
