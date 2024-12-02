# zkPass Verification with Notion Integration  

## Overview  
This project integrates **zkPass** for privacy-preserving verification and validation using the **Notion API**. It demonstrates how to create and use JSON schemas with zkPass to verify data off-chain and on-chain securely.  

The application enables:  
1. Secure proof generation using zkPass.  
2. Verification of user data on Notion pages.  
3. Integration with Ethereum (EVM-compatible) wallets for blockchain-ready verification.  

## Use Case  
This solution is ideal for any system requiring data verification from external sources, such as:  
- Authenticating data ownership in collaborative platforms like Notion.  
- Verifying credentials securely without exposing sensitive data.  
- Enabling privacy-preserving workflows for Web3 and Web2 applications.  

For example, in a decentralized credential system, users can prove ownership or access permissions to a specific Notion page without revealing its content. This approach can be extended to other APIs, making it a flexible tool for privacy-first applications.  

## Installation  

### Prerequisites  
Ensure you have:  
- Node.js (>= 18.x) and npm installed.  
- EVM-compatible wallets (e.g., MetaMask) set to the Sepolia network.  
- Two Notion accounts for testing.  
- A Notion integration set up with API access.  

### Steps  

1. **Clone the repository**:  
   ```bash  
   git clone <repository_url>  
   cd <repository_name>

2. **Install dependencies**
    ```bash  
   npm install
   
3. **Obtain Schema ID and App ID**:
   - Once the schema is created, you will be provided with a **Schema ID** and **App ID**. These IDs are unique to your schema and application and are used to generate and verify proofs for the zkPass integration.
   - Keep a copy of the **Schema ID** and **App ID**, as you will need them in the next step to configure your application.

 4: **Configure the Application with Schema ID and App ID**

After obtaining the **Schema ID** and **App ID**, you need to configure them in your project. Follow these steps:

. **Open the `App.tsx` file** in your project directory.

. **Replace the Placeholder Values**:  
   In the file, locate the variables where the **Schema ID** and **App ID** are defined. Replace them with your actual **Schema ID** and **App ID** obtained from zkPass.

   
   ## Step 5: Implement Proof Generation

- **Open the `App.tsx` file** in your project directory.
- **Add the Proof Generation Logic**:
  - Below the schema configuration, add the following logic to generate the proof:
    - Import necessary libraries for zkPass integration.
    - Use the zkPass connector to generate a proof based on the schema and user input.
  
    Example code to generate proof:
    ```typescript
    const proof = connector.generateProofMessage(
        "evm",       // Network type, for example, "evm" for Ethereum
        schemaId,    // Your Schema ID from zkPass
        userInput    // The user input data to be verified
    );
    ```

- **Handle Proof Response**:
  - Ensure that the proof generation result is correctly captured and logged for verification.

    Example:
    ```typescript
    console.log("Proof Generated", proof);
    ```

- **Save and Test**:
  - Save your changes and test the proof generation flow by running your application.
  - Ensure that the proof is generated and logged without errors.

## Step 6: Verification of Proof

- **Verification Logic**:
  - Add the verification logic right after the proof generation code to ensure that the generated proof is valid.
  - Use the zkPass connector's `verifyProofMessageSignature` method to validate the proof.

    Example verification code:
    ```typescript
    const verifiedResult = connector.verifyProofMessageSignature(
        "evm",          // Network type, such as "evm" for Ethereum
        schemaId,       // Your Schema ID from zkPass
        proof           // The proof generated from the previous step
    );
    ```

- **Handle Verified Result**:
  - If the proof is verified successfully, display a success message and update the state of your application to reflect the verified result.

    Example:
    ```typescript
    if (verifiedResult) {
        alert("Verified Result");
        setResult(proof);
    }
    ```

- **Testing Verification**:
  - Run the application and verify the proof.
  - Ensure that when the proof is valid, the verification process proceeds successfully.

## Conclusion

- **Project Summary**:
  - You have successfully set up a zkPass integration for verifying data on Notion pages.
  - The project allows you to generate and verify proofs for specific data using zkPass' zero-knowledge technology.
  
