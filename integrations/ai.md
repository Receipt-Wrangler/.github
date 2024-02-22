# Introduction

Receipt Wrangler has the ability to use OCR to pull data off of images, and AI to parse that data into a receipt. There are a couple of workflows which the user can use to create receipts quicker with AI.

## Features

### Quick Scan

The first workflow is quick scan. Quick scan is located on the receipts page, and this allows users to quickly scan a receipt, and have the data parsed into a receipt and immediately saved, taking the values result from AI.
Defaults for some of the fields can be set in user preferences, to make the process even quicker.

### Magic Fill

The next workflow is Magic Fill. Magic Fill is a way to quickly fill in a receipt from the receipt page. Once an image is uploaded, users can select an image to magic fill from. This will fill in the receipt with the values from AI, but doesn't save it right away. This allows users a chance to modify data as needed before saving.

### Email Integration

The last workflow is using the Email Integration. The Email Integration lets users send in receipts via a configured email and have them essentially Quick Scanned into the system. [Check out the documentation](https://github.com/Receipt-Wrangler/.github/tree/main/integrations) to see how to configure it.

## Configuration

config.prod.json

```json
{
  "aiSettings": {
    "type": "aiType",
    "url": "url",
    "key": "apiKey"
  }
}
```

- openAiKey: This value is the old way to provide the openAiKey and will be removed on November 1st, 2023.
- aiSettings.type: Options are openAi, gemini, or llamaGpt
- aiSettings.url: This value is only used if the the type is set to llamaGpt. F.ex, http://192.168.0.200:3000/api/v1/chat/completions
- aiSettings.key: This value is currently only used if type is set to openAi, this is replacing "openAiKey"

### Notes

The integration of LlamaGpt is what I would call very experimental, and would only attempt to use it if you have time to spare and are an advanced user. During my time playing with it, I couldn't get it to work once. However, the infrastructure is in place to theoretically support it. I ran into lots of stability issues with LlamaGpt's API as well as the results being completley incorrect and unusable.
