* Directory Hierarchy
  - Python script is provided in the "Code" folder.
  - Training studies are provided in the "training_studies" folder.
  - Test studies are provided in the "test_studies" folder.

* Requiements
  * 'Jupyter Notebook' is required to execute the script, the script can be executed using following plateforms:
    - Kaggle
    - Colab
    - Local Machine

   * Libraries Required for Local Machines: tiktoken, PyMuPDF, openai, anthropic + (pandas, re, time, os, numpy, requests, math, base64) 
   * Libraries Required for Kaggle: tiktoken, PyMuPDF, openai, anthropic

* INPUT
   - Model-Name    = claude-3-opus-20240229 / gpt-4-0125-preview / gpt-4o --- For initial testing, it is recommended to use gpt-3.5-turbo (to save the cost)
   - Model-Key     = APIKey for Cluade or GPT (purchased APIKey)
   - pdf_folder    = path to the folder that contains pdf files (in this case, for training, we provide the path to "training_studies" folder)
   - variable_file = Path to the variable file (this file contains all the variables that need to be extracted)
   - prompt_size   = Enter the number of variables for each prompt (integer number: 1, 3, 5, 10, etc.)
      - Example: If we select N=5, and # of variable=10, we will have 2 prompts (each with 5 variables) [This is a hybrid (composed/decomposed) prompting technique]
   
* OUTPUT
   The code will produce 2 files of responses
   - The first file will contain the raw responses for all the provided files and for all the variables.
   - The second file will contain the post-processed (using GPT model) responses/output.

* Disagreement-Resolution

   We used two LLMs for data extraction, according to initial results, we found that the extraction results were highly accurate when both LLMs have agreement on responses (concordant responses).
   In some cases, the responses of both LLMs were different, so we presented a solution employing a cross-critique technique where each LLM take the output responses of other LLM and verify its result.
   In most of the cases, cross-critiuqe resulted in generating concordant response.

   To execute the cross-critque code (provided at the end of the Notebook shared in the "Code" folder), you will require following information in the file:
    - File:
      Annotated Agreement Matching File
    - Information in the File:
      Variable -- GPT_Responses -- CLAUDE_Responses -- Gold_Standard -- Agree(A)/Disagree(D)

   The disagreement-resolution code will be executed twice:
   i) It will take the claude response and verify using GPT, ii) Vice-Versa

* Note
  - To execute these setting you only need to change the model name -- the script will automatically do the rest.


Contact US:
-----------
In case of any questions, please do let us know at:
riaz.irbaz@mayo.edu
ayub.umair@mayo.edu
