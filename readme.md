# Project Pipeline

This project automates the process of downloading test data, setting checkpoints, running tests, and cleaning up results using a `Makefile`. Below you can find a description of each command and how to use it.

## Table of Contents

- [Requirements](#requirements)
- [Commands](#commands)
  - [help](#help)
  - [get_data](#get_data)
  - [set-checkpoints](#set-checkpoints)
  - [test-pipeline](#test-pipeline)
  - [clean-results](#clean-results)
  - [clean-data](#clean-data)

---

## Requirements

- Python 3.x
- DVC (Data Version Control)
- Pytest
- `fteam_storage` remote configured in DVC

Ensure the above tools are installed and configured before running the Makefile commands.

---

## Commands

### `help`

Displays all available commands in the `Makefile`.

```bash
make help
