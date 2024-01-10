import time
from selenium import webdriver
from selenium.webdriver.chrome.service import Service as ChromeService
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By
class Chrome_wdn():
    def chrome_config(self):
        driver = webdriver.Chrome(service=ChromeService(ChromeDriverManager().install()))
        time.sleep(3)
        driver.maximize_window()
        time.sleep(5)
        driver.get("https://opensource-demo.orangehrmlive.com/")
        time.sleep(10)
        #driver.find_element_by_name("username").send_keys("Admin")
        driver.find_element(By.NAME,"username").send_keys("Admin")
        #driver.find_element_by_id("ypw5i").send_keys("admin123")
        driver.find_element(By.NAME,"password").send_keys("admin123")
        #driver.find_element_by_id("isz46l").click()
        driver.find_element(By.XPATH,"/html/body/div/div[1]/div/div[1]/div/div[2]/div[2]/form/div[3]/button").click()


        act_title=driver.title
        exp_title="OrangeHRM"

#obj = Chrome_wdn()
#obj.chrome_config()

        if act_title==exp_title:
            print("login test passed")
        else:
            print("login test failed")

            driver.close()

obj= Chrome_wdn()
obj.chrome_config()
