# sanitized-inputs-checker




     /my-sql-injection-checker
     ├── src
     │   ├── main.py
     │   └── utils.py
     ├── tests
     │   ├── test_main.py
     │   └── test_utils.py
     └── README.md
   


     ```python
     import re

     def check_for_sql_injection(code):
         # Simple regex to find unsanitized SQL queries
         pattern = re.compile(r"SELECT .* FROM .* WHERE .*")
         matches = pattern.findall(code)
         return matches

     if __name__ == "__main__":
         sample_code = "SELECT * FROM users WHERE username = '" + user_input + "'"
         vulnerabilities = check_for_sql_injection(sample_code)
         if vulnerabilities:
             print("Potential SQL Injection vulnerabilities found:", vulnerabilities)
         else:
             print("No vulnerabilities found.")
     ```

4. **Write Tests**:
   - In `test_main.py`, write unit tests to ensure your code works correctly.
   - Example:
     ```python
     import unittest
     from src.main import check_for_sql_injection

     class TestSQLInjectionChecker(unittest.TestCase):
         def test_no_vulnerabilities(self):
             code = "SELECT * FROM users WHERE username = 'safe_user'"
             self.assertEqual(check_for_sql_injection(code), [])

         def test_vulnerabilities_found(self):
             code = "SELECT * FROM users WHERE username = '" + user_input + "'"
             self.assertNotEqual(check_for_sql_injection(code), [])

     if __name__ == "__main__":
         unittest.main()
     ```



