# The WHO's Director General's Speeches

Below can be found a list of data retrieval scripts that help make this work possible.
# Python

All scripts have been tested on Python 3.8.6.
The external modules that were used can be found in the `requirements.txt` file along with their versions.
**Note**: not all modules are required for all scripts.
If any of the modules are not already installed the normal `pip install -r requirements.txt` process should be followed.

## Scripts

Below is a brief summary of each of the scripts.
In order to fully regenerate the results, delete the cached folder and run the scripts in the order listed.
The pathing can be changed to any desired location.

1. Open a PowerShell window and change to the `~/code` folder.
   ```{ps1}
   cd "D:\repos\WHOSpeechAnalysis\data\code"
   ```
2. [get_speeches_list](./code/get_speeches_list.py).
   This script will get the list of all of the director general's speeches from [here](https://www.who.int/director-general/speeches).
   The script can be run more than once.
   In this case the only new speeches will be retrieved.
   In the case of a network interruption causing a failed run, delete the full run and try again.
   ```{ps1}
   python get_speeches_list.py -out d:/datasets/who/raw
   ```
3. [convert_speeches_list](./code/convert_speeches_list.py).
   This script will convert the raw HTML list of links to the director general's speeches to text.
   The script can be run more than once.
   In this case the file is completly regenerated.
   ```{ps1}
   python convert_speeches_list.py -in d:/datasets/who/raw -out d:/datasets/who/speeches.txt
   ```
4. [get_speeches_text](./code/get_speeches_text.py).
   This script will get the HTML of all of the director general's speeches
   The script can be run more than once.
   In this case the only new speeches that were not previously downloaded will be retrieved.
   ```{ps1}
   python get_speeches_text.py -in d:/datasets/who/speeches.txt -out d:/datasets/who/raw
   ```
5. [convert_speeches_text](./code/convert_speeches_text.py).
   This script will convert the raw HTML speech of the director general's speeches to text.
   The script can be run more than once.
   In this case the file is completly regenerated.
   ```{ps1}
   python convert_speeches_text.py -in d:/datasets/who/raw -out d:/datasets/who/corpus.jsonl
   ```
