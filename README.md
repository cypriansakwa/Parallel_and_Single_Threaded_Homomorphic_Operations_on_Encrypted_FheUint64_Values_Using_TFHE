## Overview
- This Rust program shows how to perform homomorphic operations (addition, subtraction, multiplication, and division) on encrypted FheUint64 values using the TFHE (Tor Functional Encryption) library. The code supports both parallel and single-threaded execution modes, with Rayon used for parallel computations.
- The code improves the performance of the TFHE library by using parallel processing for homomorphic operations, which can dramatically reduce computation times for large-scale encrypted data. 
## Features
- **Homomorphic Operations:** Supports addition, subtraction, multiplication, and division on encrypted integers.
- **Execution Modes:** Choose between parallel and single-threaded execution.
- **TFHE Integration:** Uses the TFHE library for secure encryption and decryption.
- **Verification:** Compares decrypted results with plaintext calculations to ensure correctness.

## Performance Enhancement Through Parallelism
- **Parallel Execution with Rayon**
   - The Rayon library is used in the project to allow homomorphic operations to be executed in parallel. Rayon is a data parallelism library for Rust that facilitates concurrent processing and fully utilizes multi-core computers.
## How It Works
- **Parallelism Enabled:** Rayon supports parallelism, which allows operations like addition, subtraction, multiplication, and division to be performed concurrently over several threads. This enables the program to do numerous operations concurrently, which can considerably reduce total calculation time.
- **Execution Mode:** Users can select between parallel and single-threaded execution modes based on their requirements. Parallel mode is activated by calling ExecutionMode::Parallel, which causes Rayon to handle the operations concurrently. In contrast, single-threaded mode (ExecutionMode::SingleThreaded) performs actions sequentially rather than in parallel.
   - **Parallel Mode:** Parallel Mode is appropriate for instances in which numerous processes must be done simultaneously. This mode is intended to handle large-scale operations efficiently by dividing the effort among numerous threads.
   - **Single-Threaded Mode:** Ideal for testing or scenarios in which parallel execution is not required. It enables the program to execute in contexts with limited resources or in simpler cases where parallelism may not provide substantial benefits.
## Benefits
- **Improved Performance:** Parallel execution of huge datasets or complex computations can result in significant performance increases. This is accomplished by dividing the task across numerous CPU cores, which reduces processing time.
- **Efficient Resource Utilization:** Parallel processing makes the best use of available CPU cores, resulting in better resource utilization and faster execution times.
- **Scalability:** The technique scales well with the size of the dataset and the number of operations, making it appropriate for scenarios involving enormous amounts of data.
## Configuration
-Execution Modes
  - **Parallel:** Uses Rayon to parallelize operations, which can improve performance for large datasets or complex computations.
  - **SingleThreaded:** Executes operations sequentially in a single thread, which might be preferable for smaller datasets or cases where parallelism overhead outweighs benefits.
## Code Explanation
- **Configuration:** ConfigBuilder is used to configure TFHE parameters.
- **Key Generation:** generate_keys generates the client and server keys for encryption and decryption.
- **Encryption:** FheUint64::try_encrypt encrypts plaintext values.
- **Operations:** Implemented in the HomomorphicOps trait and its implementation for FheUint64.
- **Execution Modes:** ExecutionMode enum allows switching between parallel and single-threaded execution.
- **Results:** Decryption and verification of results ensure correctness.
## Example Configuration in Code
 >```
> fn parallel_homomorphic_operations(mode: ExecutionMode) -> Result<(), Box<dyn std::error::Error>> {
> // Set the execution mode here
> let mode = ExecutionMode::Parallel; // or ExecutionMode::SingleThreaded
> // Perform operations
> // ...
> }

## Requirements
- **Rust:** Ensure you have the latest stable version of Rust installed.
- **Rust version:** a minimum Rust version of $1.73$ is required to compile TFHE-rs.
- **TFHE-rs:** This project uses the TFHE-rs library for fully homomorphic encryption. It is included as a dependency in the Cargo.toml file.
- **Rayon:** The Rayon library is used for parallel processing, also included as a dependency.
``` 
#To include library run: paste the line below in 'Cargo.toml' 
#For x86_64 machine running a Unix-like OS:

tfhe = { version = "0.7.2", features = [ "boolean", "shortint", "integer", "x86_64-unix" ] }
#For ARM machine running a Unix-like OS:

tfhe = { version = "0.7.2", features = [ "boolean", "shortint", "integer", "aarch64-unix" ] }
#For x86_64 machines with the rdseed instruction running Windows:

tfhe = { version = "*", features = ["boolean", "shortint", "integer", "x86_64"] }

#ensure to build cargo after adding the tfhe library
cargo run build
```
## Usage 
- To run the program and perform homomorphic operations in parallel mode, use
 >```
>  cargo run --release --parallel
- To run the program and perform homomorphic operations in single-threaded mode, use:
 >```
>  cargo run --release --single-threaded
- By default, the code runs in parallel mode. You can switch to single-threaded mode by modifying the parallel_homomorphic_operations function call in the main function:
>```
>  fn main() -> Result<(), Box<dyn std::error::Error>> {
>  parallel_homomorphic_operations(ExecutionMode::Parallel)?; // Change to ExecutionMode::SingleThreaded for single-threaded execution
> Ok(())
> }

 ## Contributing
  - If you intend to contribute to this project, fork the repository and make a pull request.

  ## Installation

- To use this project, you need to have Rust installed on your machine.
- If Rust is not installed, follow the instructions on the [official Rust website](https://www.rust-lang.org/tools/install) to install it.
- After installing Rust, clone this repository or copy the code into a Rust project, Compile and run the code using cargo run.
## Acknowledgments
- TFHE Library
- Rayon
- Rust
  
```bash
git clone https://github.com/cypriansakwa/Parallel_and_Single_Threaded_Homomorphic_Operations_on_Encrypted_FheUint64_Values_Using_TFHE.git
cd Parallel_and_Single_Threaded_Homomorphic_Operations_on_Encrypted_FheUint64_Values_Using_TFHE
