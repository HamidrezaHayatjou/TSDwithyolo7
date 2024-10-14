
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
```

Example output:
```bash
Available commands:
  make help            - Show this help message.
  make get_data        - Download data and unzip .zip file in 'test' directory.
  make set-checkpoints - Set all checkpoints path relate to test modules in 'test' directory.
  make test-pipeline   - Run tests in the 'tests' directory.
  make clean-results   - Remove previous test result files in 'results/pipeline_testing'.
  make clean-data      - Remove test data in 'test/pipeline_testing and tests/pipeline_testing.zip'.
```

### `get_data`

Downloads the required test data from the DVC remote and unzips it in the `tests` directory.

```bash
make get_data
```

This command will:

1. Pull the `pipeline_testing.zip` file using DVC.
2. Unzip the contents into the `tests` directory.

### `set-checkpoints`

Sets the paths for all necessary checkpoints that are required by the test modules in the `tests` directory.

```bash
make set-checkpoints
```

This will:

1. Run the `set_checkpoints_path.py` script.
2. Update the checkpoint paths in the relevant test modules.

### `test-pipeline`

Runs all the test modules in the `tests` directory using Pytest.

```bash
make test-pipeline
```

This command will:

1. Clean up previous test result files.
2. Run all `.py` files inside the `tests` directory using `pytest`.
3. Display the results after all tests are completed.

### `clean-results`

Removes all the previous test result files and temporary files generated during the test process.

```bash
make clean-results
```

Files and directories removed include:

- `results/pipeline_testing`
- `tests/enhancer_training_data_temp`
- `.pytest_cache`, `__pycache__`, and logs.

### `clean-data`

Removes the test data downloaded via the `get_data` command.

```bash
make clean-data
```

This will remove:

- The `tests/pipeline_testing` directory.
- The `pipeline_testing.zip` file.

---

## Usage Example

1. Download the test data:
   ```bash
   make get_data
   ```

2. Set the checkpoints for the test modules:
   ```bash
   make set-checkpoints
   ```

3. Run the tests:
   ```bash
   make test-pipeline
   ```

4. Clean up the results after testing:
   ```bash
   make clean-results
   ```

5. Remove the test data:
   ```bash
   make clean-data
   ```

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
