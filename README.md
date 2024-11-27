# EpicChain CLI Setup and Usage Guide

A comprehensive guide for setting up and using the EpicChain Command Line Interface (CLI). The document covers system requirements, installation instructions, and usage examples for both Windows and Linux platforms. Follow the steps carefully to ensure a successful setup.

---

## Table of Contents

1. [System Requirements](#system-requirements)  
2. [Prerequisites](#prerequisites)  
   - [For Linux](#for-linux)  
   - [For Windows](#for-windows)  
3. [Downloading Pre-Compiled Binaries](#downloading-pre-compiled-binaries)  
4. [Compiling from Source](#compiling-from-source)  
   - [Cloning the Repository](#cloning-the-repository)  
   - [Compiling and Running](#compiling-and-running)  
5. [Usage Instructions](#usage-instructions)  
6. [Additional Resources](#additional-resources)  

---

## System Requirements

Before proceeding, ensure that your system meets the following requirements:

- **Operating System**  
  - Supported: **Windows** and **Linux**.  
  - Not Supported: macOS (unless using a virtual machine).  

- **Linux Compatibility**  
  - Supported: Ubuntu 14 and Ubuntu 16.  
  - Not Supported: Ubuntu 17 or other distributions not explicitly mentioned.

- **Development Environment**  
  Install the latest version of **.NET Core**, as it is required for compiling and running the EpicChain CLI. Instructions for installation are provided below.

---

## Prerequisites

To set up EpicChain CLI, specific libraries and tools must be installed based on your operating system.

### For Linux

1. **Install Required Libraries**  
   Use the following command to install `LevelDB`, `SQLite3`, and additional development dependencies:

   ```bash
   sudo apt-get install libleveldb-dev sqlite3 libsqlite3-dev libunwind8-dev
   ```

   - **LevelDB**: A fast key-value storage library used by EpicChain.  
   - **SQLite3**: A lightweight SQL database engine for managing wallet and blockchain data.  
   - **libunwind**: A library for handling stack unwinding, required by .NET Core.

2. **Install .NET Core**  
   Visit the [.NET Core official download page](https://www.microsoft.com/net/download/core) and follow the instructions to install .NET Core SDK on your Linux distribution.

---

### For Windows

1. **Install EpicChain-Compatible LevelDB**  
   Windows users must use the [EpicChain-specific version of LevelDB](https://github.com/epicchainlabs/leveldb). Download the library and follow the build instructions provided in the repository.

2. **Install .NET Core**  
   Download the Windows version of .NET Core SDK from the [official .NET Core page](https://www.microsoft.com/net/download/core) and install it on your system.

---

## Downloading Pre-Compiled Binaries

To quickly start using EpicChain CLI without compiling from source, you can download the pre-compiled binaries.

1. **Download Latest Release**  
   Visit the [EpicChain CLI Releases page](https://github.com/epicchainlabs/epicchain-cli/releases) and download the latest version of the CLI.

2. **Extract the Package**  
   Unzip the downloaded package to a directory of your choice.

3. **Run the CLI**  
   Use the following command to run the CLI:

   ```bash
   dotnet epicchain-cli.dll
   ```

---

## Compiling from Source

If you prefer to build the CLI from the source code, follow the steps below:

### Cloning the Repository

1. **Clone the EpicChain CLI Repository**  
   Use Git to clone the repository to your local machine:

   ```bash
   git clone https://github.com/epicchainlabs/epicchain-cli.git
   ```

2. **Navigate to the Repository Directory**  
   Move into the directory containing the repository:

   ```bash
   cd epicchain-cli
   ```

---

### Compiling and Running

1. **Restore Dependencies**  
   Use the `.NET Core` restore command to fetch and restore the required dependencies:

   ```bash
   dotnet restore
   ```

2. **Build the Project**  
   Compile the project in `Release` mode:

   ```bash
   dotnet publish -c Release
   ```

3. **Run the CLI**  
   After compilation, execute the following command to run the CLI:

   ```bash
   ../dotnet bin/Release/net8.0/epicchain-cli.dll
   ```

   **Note**: Replace `../dotnet` with the path to your .NET Core installation if necessary.

---

## Usage Instructions

Once the EpicChain CLI is set up, you can interact with the blockchain using various commands. Here are some common examples:

1. **Check Blockchain State**  
   Display the current state of the blockchain:

   ```bash
   show state
   ```

2. **Create a Wallet**  
   Create a new wallet file to store your cryptocurrency keys:

   ```bash
   create wallet wallet.db3
   ```

3. **Access Additional Commands**  
   Refer to the [EpicChain CLI Documentation](https://epic-chain.org/material-ui/epicchain-node/epicchain-cli/) for a complete list of commands and usage examples.

---

## Additional Resources

- [EpicChain Official Documentation](https://epic-chain.org/material-ui/getting-started/)  
- [EpicChain CLI Releases](https://github.com/epicchainlabs/epicchain-cli/releases)  
- [EpicChain Labs GitHub](https://github.com/epicchainlabs/)  

For troubleshooting or advanced configurations, consult the official documentation or reach out to the EpicChain support team.

---

This guide should serve as a complete reference for setting up and using the EpicChain CLI. For any issues or further assistance, feel free to contact [EpicChain Support](mailto:support@epic-chain.org).