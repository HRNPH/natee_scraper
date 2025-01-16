# Nattee Scraper
CEDT Comprog Automated Creation Of Testcase for vscode [CPH Extension](https://github.com/agrawal-d/cph)
designed for getting CEDT [NatteeGrader website](https://2110104.nattee.net/) testcase by reverse engineering ruby web auth of [Cafe Grader](https://github.com/cafe-grader-team/cafe-grader-web) created by T'Nattee

![showcase](https://github.com/CEDT-Chula/nattee_scraper/blob/master/showcase/showcase.gif?raw=true)

## Prerequisite
- Python 3.8 or higher
- vscode (who tf didn't have it?) or VsCodium (if you don't like microsoft)
- CPH Extension in vscode or VsCodium (if you don't like microsoft)
- Linux/MacOS preferred (Windows is not tested but if you trust ChadGPT... :D)
- This repo asssume you have basic knowledge about how to use terminal or cmd & know how to use CPH Extension

## Installation Method
### Method 1 Python Virtual Environment Installation (Recommended for Windows, as Method 2 is not tested)
```bash
git clone https://github.com/CEDT-Chula/nattee_scraper
cd nattee_scraper
python -m venv venv
# venv\Scripts\activate for windows
source venv/bin/activate # for linux/macos and unix like system
pip install -r requirements.txt
```
### Method 2 Self Compiled Binary Installation (Very Recommended for MacOS/Linux)
```bash
# This method allow you to run the program from cli "anywhere" using environment variable "path"
git clone https://github.com/CEDT-Chula/nattee_scraper
cd nattee_scraper
sudo chmod 755 ./build.sh # Give Execute Permission (for macos and linux only!)
./build.sh # for linux/macos and unix like system
# ./build.bat # for windows (btw this is not tested, this shell scripts was written by ChadGPT using build.sh as reference)
```

## Usage
1. Create some.cpp file in your vscode workspace
2. Open the file
3. Open CPH Extension
4. Press 'Create Problem' button
5. You can now use ntscraper to get testcase from NatteeGrader!
### Supported URLs
|Type| Example |
|--|--|
|Submission Page| https://2110104.nattee.net/submissions/direct_edit_problem/[id] |  
|Testcases Page|  https://2110104.nattee.net/testcases/show_problem/[id]|  
### Execution Command
```bash
# 1st time
executable [path/to/file.cpp] --quiz_testcase_link [url] --uid [your_login_uid] --password [your_login_password]
# 2nd time
executable [path/to/file.cpp] --quiz_testcase_link [url] # no need to type uid and password again
```
- password and uid will be cached temporarily in your system cache(temp) folder so you don't have to retype it again
- if you want to change your uid or password, just use the full command again with the new uid and password



### Python installation Example
```bash
# python installation
python ntscraper.py ./file.cpp --quiz-testcase-link https://2110104.nattee.net/submissions/direct_edit_problem/1307 --uid 66778899 --password 12345678
```
### Binary installation Example
```bash
# binary installation
ntscraper ./file.cpp --quiz_testcase_link https://2110104.nattee.net/testcases/show_problem/1307 --uid 66778899 --password 12345678
```
<details>
<summary>command not found: ntscraper ?</summary>

    after the build move the ntscraper from 'nattee_scraper/dist' to the path that you want to execute the scraper from
</details>
<br>

### Folder-based Test Case Import (No login required)

If you have test cases stored locally in a folder (with `.in` files for inputs and `.sol` files for outputs), you can bypass logging into NatteeGrader by using the `--folder` argument.

Each test case file pair should follow the naming convention `x.in` for input and `x.sol` for the expected output, where `x` is a numeric identifier for the test case.

#### Example Usage:
```bash
# Use this command to create test cases from a local folder
python ntscraper.py ./file.cpp --folder ./path_to_test_cases_folder
```

#### Example Local Test Case Folder Structure:
```bash
path_to_test_cases_folder
├── 1.in
├── 1.sol
├── 2.in
├── 2.sol
```

# Contribution Needed
- Testing And Fix (if it broke) build.bat on windows (please also update the docs na bro)
- Improvements On Codebase Algorithm & Maybe Some Refractor
- Add Functionality To Improve Users Experience Such As (Multi Quizs Testcase Generation)
