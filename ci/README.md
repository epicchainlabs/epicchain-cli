# Test & Continuous Integration (CI) Setup for EpicChain CLI

This section outlines the process for running the test suite for the EpicChain CLI both manually and automatically through Continuous Integration (CI) using [Travis CI](https://travis-ci.org/epicchainlabs/epicchain-cli). These tests ensure the functionality and reliability of the EpicChain CLI codebase.

---

## Overview

The test suite is designed to:

1. Build the latest version of the EpicChain CLI code.
2. Perform functional tests on the CLI using [expect](https://linux.die.net/man/1/expect) scripts.
3. Verify JSON-RPC capabilities using `curl`.

The tests can be run locally or automatically triggered via Travis CI upon each code push to the repository.

---

## Running Tests Manually

To run the tests manually on your development machine, follow these steps:

### Prerequisites

1. **Install Docker Community Edition (CE)**  
   Docker CE is required to create a containerized environment for testing. Download and install Docker CE from the [official Docker website](https://www.docker.com/community-edition#/download).

2. **Use a Bash-Compatible Shell**  
   The test script requires a Bash-compatible shell to execute. Examples include:
   - **Linux Shells**: Default terminal for most Linux distributions.
   - **Git Bash**: For Windows users, install [Git Bash](https://gitforwindows.org/) to provide a Bash environment.

---

### Running the Test Suite

1. Clone the EpicChain CLI repository if you haven’t already:

   ```bash
   git clone https://github.com/epicchainlabs/epicchain-cli.git
   cd epicchain-cli
   ```

2. Execute the test script:

   ```bash
   ./ci/build-and-test.sh
   ```

   This command performs the following tasks:
   - Builds the Docker image using the provided `Dockerfile`.
   - Runs the EpicChain CLI tests inside the Docker container.

---

## Continuous Integration with Travis CI

The test suite is configured to run automatically via Travis CI on every code push to the repository. Travis CI ensures code integrity by executing the test suite in a controlled environment, detecting issues early in the development process.

### CI Process Flow

1. Code is pushed to the EpicChain CLI repository.
2. Travis CI triggers the test suite, which:
   - Builds the EpicChain CLI code.
   - Executes functional and JSON-RPC tests.
3. The test results are reported directly on the Travis CI dashboard.

For more information, visit the [Travis CI configuration for EpicChain CLI](https://travis-ci.org/epicchainlabs/epicchain-cli).

---

## Key Test Files

The test suite relies on the following files and scripts:

1. **`Dockerfile`**  
   - Defines the Docker environment used for building and testing the EpicChain CLI.
   - Specifies all necessary dependencies and configurations.

2. **`ci/build-and-test.sh`**  
   - The primary script that:
     - Builds the Docker image.
     - Starts the container.
     - Executes all tests inside the container.  
   - Useful for replicating CI tests on local machines.

3. **`ci/run-tests-in-docker.sh`**  
   - Executes within the Docker container.
   - Handles the internal testing procedures such as running CLI commands and verifying outputs.

4. **`ci/test-epicchain-cli.expect`**  
   - An `expect` script used for functional verification of the CLI.
   - Simulates user interactions and validates the behavior of the EpicChain CLI.

5. **`ci/test-jsonrpc.sh`**  
   - Uses `curl` to validate JSON-RPC functionality, ensuring API compatibility.

---

## Test Coverage

The following aspects of the EpicChain CLI are verified:

1. **Basic Functionality**  
   Tests core commands to ensure the CLI operates as expected.

2. **JSON-RPC API**  
   Validates the JSON-RPC interface, ensuring proper communication with external applications.

3. **Build Process**  
   Confirms that the CLI builds without errors in the specified environment.

---

## Troubleshooting and Notes

1. **Docker Issues**  
   - Ensure Docker is installed and running correctly. Test it by running `docker --version`.
   - If you encounter permission errors, try running the command with `sudo` (Linux) or ensure your user account is part of the `docker` group.

2. **Testing Locally**  
   Running the tests manually with `build-and-test.sh` replicates the CI environment, making it an excellent way to debug failures.

3. **Expect Dependency**  
   The `expect` scripting language is required for certain functional tests. Ensure it is installed on your system. On Linux, install it using:

   ```bash
   sudo apt-get install expect
   ```

---

## Additional Resources

- [Docker Installation Guide](https://docs.docker.com/get-docker/)  
- [Travis CI Documentation](https://docs.travis-ci.com/)  
- [Expect Command Reference](https://linux.die.net/man/1/expect)

For further questions or issues, please contact the EpicChain development team or open an issue on the [GitHub repository](https://github.com/epicchainlabs/epicchain-cli/issues).