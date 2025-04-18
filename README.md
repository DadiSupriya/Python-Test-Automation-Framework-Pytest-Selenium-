from pages.login_page import LoginPage

def test_login_valid(browser):
    login_page = LoginPage(browser)
    login_page.go_to_login_page()
    login_page.enter_username("tomsmith")
    login_page.enter_password("SuperSecretPassword!")
    login_page.click_login()

    assert "secure" in browser.current_url
from selenium.webdriver.common.by import By

class LoginPage:
    def __init__(self, driver):
        self.driver = driver
        self.username_input = (By.ID, "username")
        self.password_input = (By.ID, "password")
        self.login_button = (By.CLASS_NAME, "radius")

    def go_to_login_page(self):
        self.driver.get("https://the-internet.herokuapp.com/login")

    def enter_username(self, username):
        self.driver.find_element(*self.username_input).send_keys(username)

    def enter_password(self, password):
        self.driver.find_element(*self.password_input).send_keys(password)

    def click_login(self):
        self.driver.find_element(*self.login_button).click()
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options

def init_driver():
    options = Options()
    options.add_argument("--headless")  # Run in headless mode (no GUI)
    service = Service()
    driver = webdriver.Chrome(service=service, options=options)
    driver.implicitly_wait(10)
    return driver
import pytest
from utils.browser_setup import init_driver

@pytest.fixture
def browser():
    driver = init_driver()
    yield driver
    driver.quit()
selenium
pytest
pip install -r requirements.txt
# Python Test Automation Framework

A simple, modular test automation framework using **Python**, **Pytest**, and **Selenium**.

## Features
- Page Object Model
- Pytest fixtures
- Headless browser testing

## Install Dependencies
```bash
pip install -r requirements.txt
pytest tests/

---

✅ Once you paste these files into your local folder, you can follow the Git commands I mentioned earlier to push it to GitHub.

Want help creating the **RPA** sample next?
