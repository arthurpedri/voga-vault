## Assert
- Basic pattern: ==assert \<condition>, 'Message if condition is not met'==
- Assert will throw an *AssertionError* if the condition evaluates to false with the failure message.

```python
import unittest # std lib module for unit testing

# Function that gets tested
def times_ten(number):
    return number * 100

# Test class
class TestTimesTen(unittest.TestCase):
    def test_multiply_ten_by_zero(self): # tests have to start with 'test'
        self.assertEqual(times_ten(0), 0, 'Expected times_ten(0) to return 0')

    @unittest.skipIf(not sys.platform.startswith("linux"), "This test only runs on Linux")
    def test_multiply_ten_by_one_million(self):
        # test can also be skipped using the method self.skipTest('Message'), usually with complex conditions
        self.assertEqual(times_ten(1000000), 10000000, 'Expected times_ten(1000000) to return 10000000')

    @unittest.expectedFailure # will succeed if the test fails and fails if it passes
    def test_multiply_ten_by_negative_number(self):
        self.assertEqual(times_ten(-10), -100, 'Expected add_times_ten(-10) to return -100')

    def extra_assertions():
        self.assertIn(value, container) # value found in the container
        self.assertTrue(value) # value true
        self.assertLess(value1, value2) # checks if value1 is less than value 2
        self.assertAlmostEqual(value1, value2) # checks if they are equal when rounded to 7 decimal places
        # the asserts for raises and warns are difficult to replicate using assert, so using them is recommended
        self.assertRaises(TypeError, funct, function_args) # calls the function and passes if the exception is raised
                                                           # is an error if another exception is raised
                                                           # fails if no exception is raised
        self.assertWarns(specificWarningException, function, function_args) # same as raises but with warnings

# Run the tests
unittest.main()
```
- Tests can also be skipped using the method ==self\.skipTest('Message')==, usually with more complex conditions.
### Test Decorators
-  ==@unittest\.skipIf(condition, msg)==: Will skip the test if the condition is ==true==.
- ==@unittest\.skipUnless(condition, msg)==: Will skip the test if the condition is ==false==.
-  ==@unittest\.expectedFailure==: Will succeed if the test fails and fails if it passes.
### Subtest Context Manager
-  Will run each iteration as an individual test.
- using *num* as parameter will show the number on the traceback instead of (\<subtest\>).
```python
    def test_times_ten(self):
        for num in [0, 1000000, -10]:
            with self.subTest(num): 
                expected_result = num * 10
                message = 'Expected times_ten(' + str(num) + ') to return ' + str(expected_result)
                self.assertEqual(times_ten(num), expected_result, message)
```
### Test fixtures 
- Assures predictable states for the tests.
```python
    def setUp(self):
        print('This will run BEFORE EVERY single test, and the method is detected by the framework')

    @classmethod
    def setUpClass(cls):
        print('This will run once BEFORE ALL the tests in the class, and the method is detected by the framework')

    def tearDown(self):
        print('This will run AFTER EVERY single test, and the method is detected by the framework')

    @classmethod
    def tearDownClass(self):
        print('This will run once AFTER ALL the tests in the class, and the method is detected by the framework')

```