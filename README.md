# Dockerfile Bug: COPY before RUN

This repository demonstrates a common error in Dockerfiles: using the `COPY` instruction before the `RUN` instruction to install dependencies. This can lead to issues where the copied files are not available during the dependency installation, causing build failures.

## Bug

The original Dockerfile attempts to copy the `requirements.txt` file before installing `python3` and `pip`, which leads to a build failure because the interpreter and package manager are not yet available.

## Solution

The corrected Dockerfile installs the interpreter and package manager first, ensuring that the `requirements.txt` file can be correctly processed when the `RUN pip3 install -r requirements.txt` instruction is executed.