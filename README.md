# PyAutoFlashCard

A llm based approach to generate (wrong) example answers for Flash cards. This is for a simple game where the user
has to choose between multiple answers, of which only one is correct. The other answers are generated locally by gpt-2.

This is within the intended usecase of early large language models, since they should only be used where answers just
have to look correct but not actually be true ("hallucination"). The idea behind this project is to use this weakness
of large language models to our advantage, since for a "who wants to be a millionaire"-type quiz you require answers
that look right in terms of syntax, but ones that aren't necessarily correct.

# Installation

- #### (1) creating the virtual environment

    First: create a new anaconda environment

    ```
    conda create -n PyAFC python=3.7
    ```
  
    Then activate the virtual environment

    ```
    conda activate PyAFC
    ```
  
    Now install all the required packages as follows:
    
    ```
    python -m pip install tensorflow==1.13.1
    ```
  
    ```
    python -m pip install fire==0.1.3
    ```
  
    ```
    python -m pip install requests==2.21.0
    ```
  
    ```
    python -m pip install tqdm==4.31.1
    ```
  
    ```
    python -m pip install protobuf==3.20.0
    ```
  
    ```
    python -m pip install regex
    ```
  
    If you don't already have git installed on your system, you can install it in your conda environment now as you will
    need it later

    ```
    conda install git
    ```

- #### (2) locally installing gpt-2
    
    This is based on the following tutorial:
    https://timhanewich.medium.com/running-openais-gpt-2-language-model-on-your-pc-5d5e1b9fbb8b

    The technical details of the used language model are not part of the scope of this project since it is only used
    as an external resource!

    Before continuing you should create a directory for this project and cd into it, then run all the following commands
    from that path so everything is in one place.
    
    ```
    git clone https://github.com/openai/gpt-2
    ```
  
    Now cd into the directory you cloned this repo to and download the desired model

    ```
    cd gpt-2
    ```

    ```
    python download_model.py 774M
    ```

    (~3GB). Smaller Models are available (down to ~500MB). For help, see the arcticle linked above.

- #### (3) installing this repository

    ```
    git clone https://github.com/MaximilianNast/PyAutoFlashCard
    ```

- #### (4) modifying gpt-2 interaction

    The cloned github repository for gpt-2 provides an interactive ("Chat-Like") command line interface. We don't
    need this, since we will invoke the model directly from code without user input.

    That's why this repository provides a slightly modified way to interact with the model. To use it, copy

    ```
    C:/.../PyAutoFlashCard/interactive_conditional_samples_mod.py
    ```
  
    to

    ```
    C:/.../gpt-2/src
    ```


# Usage

- You are now ready to use PyAutoFlashCard. Configure the IDE of your choice to run

  ```
  C:/.../PyAutoFlashCard/main.py
  ```

  with the previously configured anaconda environment.


- Alternatively, run it from the command line like this:

  ```
  conda activate PyAFC
  ```
  
  ```
  cd C:/.../PyAutoFlashCard
  ```
  
  ```
  python main.py
  ```

- If everything is set up correctly, this should generate answers based on the context and question defined in main.py.
  It will then ask you to choose the correct answer from the options given to you and lastly tell you whether you're
  correct or not.

- Warning: The generation of answers might take a few seconds based on the size of model you chose, your CPU and the
  parameters you configured in main.py. It may also generate a few warnings.

# demo

![img4](https://github.com/MaximilianNast/PyAutoFlashCard/tree/main/demo_imgs/Screenshot_4.png?raw=true)