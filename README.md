# Vector Storage 

A simple and efficient vector database that stores document vectors in the browser's local storage. This package allows you to perform similarity searches on text documents using vector embeddings. It uses OpenAI embeddings to convert text documents into vectors and provides an interface for searching similar documents based on cosine similarity.

## Features

- Store and manage document vectors in local storage
- Perform similarity searches on text documents
- Filter search results based on metadata or text content
- Automatically manage storage size and trim documents when needed

## Installation

Install the package using npm:

```bash
npm install vector-storage
```

##Usage
Here is a basic example of how to use the VectorStorage class:

```javascript
import { VectorStorage } from 'vector-storage';

// Create an instance of VectorStorage
const vectorStore = new VectorStorage({ openAIApiKey: 'your-openai-api-key' });

// Add a text document to the store
await vectorStore.addText('The quick brown fox jumps over the lazy dog.', { category: 'example' });

// Perform a similarity search
const results = await vectorStore.similaritySearch({ query: 'A fast fox leaps over a sleepy hound.' });

// Display the search results
console.log(results);
```

## API

### `VectorStorage`

The main class for managing document vectors in local storage.

#### `constructor(options: IVectorStorageOptions)`

Creates a new instance of `VectorStorage`.

- `options`: An object containing the following properties:
  - `openAIApiKey` (required): The OpenAI API key used for generating embeddings.

#### `addText(text: string, metadata: object): Promise<void>`

Adds a text document to the store.

- `text`: The text content of the document.
- `metadata`: An object containing metadata associated with the document.

#### `addTexts(texts: string[], metadatas: object[]): Promise<void>`

Adds multiple text documents to the store.

- `texts`: An array of text contents for the documents.
- `metadatas`: An array of metadata objects associated with the documents.

#### `addDocuments(documents: IDocument[]): Promise<void>`

Adds multiple documents to the store.

- `documents`: An array of document objects, each containing text, metadata, and other properties.

#### `similaritySearch(params: ISimilaritySearchParams): Promise<IDocument[] | [IDocument, number][]>`

Performs a similarity search on the stored documents.

- `params`: An object containing the following properties:
  - `query`: The query text or vector for the search.
  - `k` (optional): The number of top results to return (default: 4).
  - `filterOptions` (optional): An object specifying filter criteria for the search.
  - `withScore` (optional): A boolean indicating whether to return similarity scores with the results (default: false).

## Contributing

Contributions to this project are welcome! If you would like to contribute, please follow these steps:

1. Fork the repository on GitHub.
2. Clone your fork to your local machine.
3. Create a new branch for your changes.
4. Make your changes and commit them to your branch.
5. Push your changes to your fork on GitHub.
6. Open a pull request from your branch to the main repository.

Please ensure that your code follows the project's coding style and that all tests pass before submitting a pull request. If you find any bugs or have suggestions for improvements, feel free to open an issue on GitHub.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for the full license text.

Copyright (c) Nitai Aharoni. All rights reserved.

