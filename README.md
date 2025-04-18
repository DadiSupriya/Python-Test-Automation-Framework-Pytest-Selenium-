from pages.login_page import LoginPage

def test_login_valid(browser):
    login_page = LoginPage(browser)
    login_page.go_to_login_page()
    login_page.enter_username("tomsmith")
    login_page.enter_password("SuperSecretPassword!")
    login_page.click_login()

    assert "secure" in browser.current_url

