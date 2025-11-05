# gRPC-Web Tester

`grpc-test.html` is a **client-side, single-page tool** for quickly testing and validating gRPC `.proto` definitions directly in the browser — without needing any backend service or build tools.

It allows you to:
- Load `.proto` files from disk or paste them into the editor.
- Parse the `.proto` definition structure using [protobuf.js].
- Inspect defined **packages**, **services**, and **methods**.
- Experiment with gRPC request structures.
- Export the current edited `.proto` back to a file.
- Send the request to specified server and get the response / stream of responses back (you need gRPC server for that)

All logic is performed **entirely in the browser**, using pure HTML, CSS, and JavaScript.

---

## 🧩 Features

- **Import `.proto` files** — reads and displays file content in an editor.
- **Parse Proto** — uses `protobuf.js` to analyze definitions and show available services and RPC methods.
- **Service/Method Selection** — dynamically populates dropdowns based on the parsed content.
- **Export Proto** — saves current editor content as a `.proto` file (`exported.proto`).
- **No backend required** — runs completely client-side.
- **Clear status messages** — visual feedback for loading, parsing, and exporting steps.
- **Automatic UI updates** — once a valid proto is parsed, the app updates service/method dropdowns automatically.

---

## 🧠 How It Works

1. When a `.proto` file is selected, JavaScript reads it using the `FileReader` API.
2. The contents are displayed in a `<textarea>` for optional manual editing.
3. On pressing **“Parse Proto”**, the text is parsed by `protobuf.js`:
   - The `protobuf.parse()` method creates an in-memory `Root` object.
   - Services are recursively discovered in nested namespaces.
   - Found service and method names populate dropdown selectors.
4. The **“Export Proto”** button allows the current text to be downloaded as a `.proto` file via a dynamically generated Blob URL.
5. All updates (status info, success/error messages) are shown inline under the editor.

---

## ⚙️ Technologies Used

| Component | Purpose |
|------------|----------|
| **HTML5** | Provides the single-page structure, layout, and interactive form elements. |
| **CSS3** | Implements a clean, minimal UI — with light shadows, rounded corners, and visual feedback colors. |
| **JavaScript (ES6)** | Drives all logic for parsing, UI updates, file I/O, and status handling. |
| **[protobuf.js](https://github.com/protobufjs/protobuf.js)** | A pure JavaScript Protocol Buffers implementation used for `.proto` parsing and introspection. |
| **Blob & File APIs** | Enable client-side export and import of `.proto` files without any server. |

---

## 🧭 Usage Instructions

1. Open `grpc-test.html` in any modern browser (Chrome, Edge, Firefox).
2. Either:
   - Click **“Import .proto”** to load a local file, or  
   - Paste or edit `.proto` text directly in the editor box.
3. Click **“Parse Proto”** to analyze the structure.
4. Select a service and RPC method (if defined) to view details.
5. Optionally edit the text.
6. Click **“Export Proto”** to download the current text as a `.proto` file.

---

## 📄 License

This utility is free for personal and educational use.
You can modify and extend it for your own gRPC testing or teaching needs.

Created as a lightweight gRPC exploration tool powered by [protobuf.js] and plain web technologies.
