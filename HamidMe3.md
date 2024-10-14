
# Module Testing Guide

For use Individually, you need to set the address of the input images in the relevant module. For use collectively, you can use the `makefile` in the main directory of the project. In both cases, you can test a different combination of parameters and you need to make the corresponding changes in the files.

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

To run tests for all modules at once, you can utilize the `Makefile` in the project's root directory. Follow the steps below:

1. Ensure that all necessary data and checkpoints are available by pulling them using `dvc`:
   ```bash
   dvc pull -r fteam_storage tests/pipeline_testing.zip.dvc
   ```
2. Extract the test data:
   ```bash
   unzip -o tests/pipeline_testing.zip -d $(dir tests/pipeline_testing.zip)
   ```
3. Set the correct checkpoints for all modules:
   ```bash
   make set-checkpoints
   ```
4. Run all tests using the `Makefile`:
   ```bash
   make test-pipeline
   ```

This will execute all test scripts located in the `tests` directory and display the results.
