# QA-Turk: Annotation tool for Extractive Question Answering with localturk / Amazon Mechanical Turk

Adapted from [Vicor Quach](https://github.com/Varal7)) great [ieturk](https://github.com/Varal7/ieturk) repo.

## Input Files

Requires a CSV input file with `description`,`question`,`spans` input. Spans are `start,end` token tuples that will be prefilled in the interface.

Notes:
- Multiple spans are specified as `start_1,end_1,start_2,end_2,...`.
- No spans are specified as "".
- Use a standard CSV reader/writer to make sure everything is escaped properly.
## Annotate

### Annotate using Mechanical Turk

- Create an new project in [Amazon Mturk interface](https://requester.mturk.com/create/projects/new).
- Paste the content of `annotate.html` in the second tab `Design layout`.
- Insert the scripts `config.js`, `annotate.js` and the CSS file `style.css` into the document as well
- Prepare a tokenized version of the entry, splitting characters with `>>`.
- Submit batch

### Annotate locally

Requires [localturk](https://github.com/danvk/localturk). Install using

```
npm install -g localturk
```

Modify `config.js` with the name of the fields of interest.
Then simply run it using the same tokenized csv file as for Mechanical Turk.

```
localturk annotation.html input.csv output.csv
```

## Visualize

Simply open `visualize.html` with any modern browser.
Then choose the `.csv` that came from either localturk or Mechanical Turk.