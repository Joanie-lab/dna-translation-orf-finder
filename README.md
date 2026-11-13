# DNA Translation and ORF Finder

A beginner project that reads DNA sequences from a FASTA file, finds open reading frames (ORFs), and translates the longest one into a protein.

## What it does
- Finds ORFs: stretches that start with a start codon (ATG) and end with an in-frame stop codon (TAA, TAG or TGA)
- Ignores ORFs shorter than a minimum length (default 60 letters)
- Reports the longest ORF and translates it into amino acids
- Handles missing files, empty sequences, sequences with no ORF and unexpected characters

## Example
Input: human insulin mRNA (NM_000207.3) from NCBI, 465 letters.

```
Name: NM_000207.3
Sequence length: 465
ORFs found (min length 60): 2
Longest ORF: start 59 | end 392 | length 333
Protein length: 110 amino acids
Protein (first 30): MALWMRLLPLLALLALWGPDPAAAFVNQHL
```

## Validation
The translated protein was compared with human preproinsulin from UniProt (P01308). The two sequences match exactly, at 110 amino acids.

## Files
- `dna_translation_orf.ipynb`: the Google Colab notebook with the code and documentation

## How to run it
1. Open the notebook in Google Colab.
2. Run all cells (Runtime → Run all).
3. To analyse your own sequence, upload a FASTA file and run `analyse_orfs("your_file.fasta")`.

## Limitations
- Searches the forward strand only, so genes on the reverse strand are missed
- Uses ATG as the only start codon
- Does not handle introns, so it suits mRNA or cDNA better than raw genomic DNA
- Uses the standard genetic code only
- Reports nested ORFs separately

## Possible extensions
- Search all six reading frames, using the reverse complement
- Compare results with Biopython and NCBI's ORFfinder
- Plot ORF lengths with matplotlib

## What I learned
Applying Python (functions, loops, dictionaries and error handling) to a biological problem: the genetic code, reading frames, and validating results against a trusted database.
