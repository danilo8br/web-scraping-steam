# web-scraping-steam
Steam Web Scraping using Python and Selenium.

The goal of the project is to take data from Steam with Python and Selenium and send it to a file. The beauty of this project is to get data from each page with an automated click

- First of all before starting the project, you have to install chromedriver with the current version of your google chrome. To be controlled by automated software to interact with the test script.

- Once installed, it has to be in the same directory as your file that will be made the script.

- Download link: https://chromedriver.chromium.org/downloads

# Let's go to the code

### Modules 

Importing libraries

<details><summary>Selenium</summary>
  Importing the Selenium library webdriver.
</details>

```
from selenium import webdriver
```

<details><summary>Sleep</summary>
  Importing Sleep from the Time library
</details>

```
from time import sleep
```

### Chrome interaction

Interacting with chrome and taking the page we are going to use.

<details><summary>Webdriver</summary>   
  Interacting and taking the page
</details>

```
driver = webdriver.Chrome('chromedriver')
driver.get('https://store.steampowered.com/games/?l=brazilian')
```

### Developing the function 

This function sends the data to the steam.csv file (if the file does not exist, it will be created).
The function will take 15 elements from the page and the data are name, price, discount and description.

<details><summary>Function one</summary>
  Getting the data
</details>

```
def le_jogos():
    with open('steam.csv','a', encoding='utf-8') as file:
        for c in range(1, 16):
            nome = driver.find_element_by_xpath(f'//*[@id="NewReleasesRows"]/a[{c}]/div[3]/div[1]').text
            try:
                preco = driver.find_element_by_xpath(f'//*[@id="NewReleasesRows"]/a[{c}]/div[2]/div[2]/div[2]').text
            except:
                preco = driver.find_element_by_xpath(f'//*[@id="NewReleasesRows"]/a[{c}]/div[2]/div/div').text
            desconto = driver. find_element_by_xpath(f'//*[@id="NewReleasesRows"]/a[{c}]/div[2]/div[1]').text
            descricao = driver.find_element_by_xpath(f'//*[@id="NewReleasesRows"]/a[{c}]/div[3]/div[2]/div').text
            file.write(nome+'; '+preco+'; '+desconto+'; '+descricao+"\n")
```
