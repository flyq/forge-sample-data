# Sample Circom Circuits

In this directory, we provide a handful of Circom circuits which have already been prepared to use with Forge.  You may find them useful as a reference when writing your own circuits; or you may use these as circuit uploads if you are just beginning to try out Forge.

All of the tar files are compressed versions of the corresponding folder (except for `foodie` which has all the circuit code in a subfolder).  Rather than uploading the entire directory to Forge, you will upload it's compressed `.tar.gz` file.  In order to request a proof for one of these circuits, consult the `input.json` file in the corresponding folder.  

It is allowed (but unneccesary) to include extraneous files in your compressed directory.  For instance, we have included readme's and example inputs.  All files except `circuit.circom` and any Circom files that it references are ignored.

See Sindri's GitBook for more complete instructions. 

## Available Circuits

| Name | Size (# Constraints) | Original Source | Functionality | 
| ---- | ---- | --------------- | ------------- | 
| multiplier2 | 1 | [Circom2 Docs](https://docs.circom.io/getting-started/writing-circuits/)| Computes the product of two private inputs| 
| sha256      | 152313 | [Celer Network's Benchmarking](https://github.com/celer-network/zk-benchmark/tree/main) | Verifies that the SHA256 hash of a private preimage equals the claimed public output|
| sudoku      | 11906 | [Web3-Master's ZK-Sudoku](https://github.com/web3-master/zksnark-sudoku)| Trustless verification of a Sudoku solution |
| foodie      | 60530 | Original DNN + [Keras2Circom](https://github.com/socathie/keras2circom) transpiler | Verified inference with a dense neural network |



## Circuit Requirements
- The main component file of your circom circuit must be named `circuit.circom`
- All code imports must use relative paths

## Structure
```
my_repo/
    circuit.circom
    supplementary.circom
```
Note that you may have nested directories within the parent, as long as `circuit.circom` sits at the first level.  A common convention when developing locally is to store all `circomlib/` templates in one place and import them for any specific circuit via a relative path resembling `../../circomlib/etc.circom`.  When preparing your circuit for upload, you may find it useful to include a `circomlib` folder with the necessary files (the sudoku circuit code gives an example of this.)

## How to compress properly
To prepare your repo, `my_repo`, for Forge upload, run the following command ***from the parent directory*** of `my_repo`:
```
tar -zcvf my_repo.tar.gz my_repo/
```
*Note: The `my_repo` portion of `my_repo.tar.gz` may be called anything.*

## Invalid compression example
Your repo may only have 1 circom file. Do not compress only the `circuit.cirom` file. You must still compress the entire repo directory.

Example structure (only 1 circom file):
```
my_repo/
    circuit.circom
```

Invalid compression:
```bash
# INVALID
cd my_repo/
tar -zcvf my_repo.tar.gz circuit.circom
```
