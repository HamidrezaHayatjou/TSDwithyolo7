
# Module Testing Guide

For use Individually, you need to set the address of the input images in the relevant module. For use collectively, you can use the `Makefile` in the main directory of the project. In both cases, you can test a different combination of parameters and you need to make the corresponding changes in the files.

## Test modules individually

Before testing a specific module, ensure that:

1. The required weights have been pulled using `dvc`.
2. The module's checkpoint paths are correctly set in the corresponding `.yaml` file.

To test an individual module:

1. Navigate to the `tests` directory.
2. Run the following command:
   ```bash
   pytest -v test__module.py
   ```
   Replace `test__module.py` with the name of the specific module you want to test.

## Testing All Modules at Once

To run tests for all modules at once, you can utilize the `Makefile` in the project's root directory. The description of `Makefile` is as follows:

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
