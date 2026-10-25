# FileConvert — Browser-Based File Converter

FileConvert is a React application for converting documents and images directly in the browser. It offers file previews where applicable, a format selector, conversion status/error feedback, and downloadable results—without uploading selected files to a conversion server.

## Supported conversions

| Input | Output | Notes |
| --- | --- | --- |
| `.doc` | PDF | Legacy Word extraction is best-effort and may not preserve formatting |
| `.docx` | PDF | Extracts document content in the browser before generating a PDF |
| PDF | `.docx` | Creates a new Word document; complex layout may not be preserved |
| JPG/JPEG | HEIC | Browser-side image conversion |
| HEIC/HEIF | JPG | Browser-side image conversion |

Files larger than 50 MB are rejected. Documents larger than 25 MB are also rejected by the current validation because conversion can be memory-intensive.

## Technology

- React 19, TypeScript, Vite 8
- Tailwind CSS 4 using the Vite plugin
- Mammoth, jsPDF, docx, and heic2any for browser-side document/image processing
- ESLint

## Run locally

Prerequisites: a recent Node.js release compatible with Vite 8 and npm.

```bash
git clone https://github.com/Swamiviresh/Convert.git
cd Convert
npm install
npm run dev
```

Open the local URL printed by Vite, usually [http://localhost:5173](http://localhost:5173).

## Scripts

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Run TypeScript project checks and create the production bundle |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |

## Privacy and limitations

- Conversion runs in the browser; this repository does not contain a file-conversion API or server upload flow.
- Large files can use significant browser memory and may be slower on mobile devices.
- Legacy `.doc` extraction and PDF-to-DOCX conversion can lose layout, fonts, and other formatting.
- No backend database or environment variables are required for the listed conversions.
