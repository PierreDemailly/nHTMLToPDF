# nHTMLToPDF
Node lib for converts HTML with dynamic or static content or url to PDF files

## Installation
```$ npm install @rossbob/html-to-pdf```

## Unit Test
- Jest
- Coverage : 100%

## Usage

```js
async function main() {
  try {
    const browser = await pdf.initBrowser();
    const pdfs = await pdf.generatePDF(browser, files);
    const pdf = await pdf.generatePDF(browser, file);

    const stream = await fs.createWriteStream(`./${your_pdf_name}.pdf`);

    await stream.write(pdf.buffer); // => create file for the given buffer.
    
    for (let file of pdfs) {
      await stream.write(file.buffer); // => create file for each given buffer
    }

    await pdf.terminateBrowser;
  } catch (error) {
    throw new Error(error);
  }
}
main().catch(console.error);
```

### initBrowser(): Promise<Browser>

```js
async function main() {
  try {
    const browser = await pdf.initProcess();
  } catch (error) {
    throw new Error(error);
  }
}
main().catch(console.error);
```

### generatePDF(browser: Browser, files: pdfFile[], options?: PDFOPtions): Promise<PDF[]>

```ts
interface pdfFile {
  content?: string,
  url?: string,
  options?: {}
}

More Info [there](https://pptr.dev/#?product=Puppeteer&version=v7.1.0&show=api-pagepdfoptions)
interface PDFOptions {
  path?: string,
  scale?: number,
  displayHeaderFooter?: boolean,
  headerTemplate?: string,
  footerTemplate?: string,
  printBackground?: boolean,
  landscape?: boolean,
  pageRanges?: string,
  format?: string,
  width?: string | number,
  height?: string | number,
  margin?: {
    top?: string | number,
    right?: string | number,
    bottom?: string | number,
    left?: string | number,
  },
  preferCSSPageSize?: boolean
}

interface PDF {
  options?: string,
  buffer: Buffer
}
```

```js
async function main() {
  try {
    const browser = await pdf.initBrowser();
    const result1 = await pdf.generatePDF(browser, files);
  } catch (error) {
    throw new Error(error);
  }
}
main().catch(console.error);
```

### terminateBrowser(browser: Browser): Promise<void>

```js
async function main() {
  try {
    const browser = await pdf.initBrowser();
    await pdf.terminateBrowser
  } catch (error) {
    throw new Error(error);
  }
}
main().catch(console.error);
```

### How to use [Zup](https://github.com/mscdex/zup)
