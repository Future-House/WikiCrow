# WikiCrow
WikiCrow is an automated system from [Future House](https://www.futurehouse.org/), that can synthesize cited and accurate Wikipedia-style summaries for technical topics from the scientific literature. Wikicrow is built on top of [PaperQA](https://github.com/whitead/paper-qa), a Retrieval-Augmented Generative (RAG) agent. 

## Prompts - Section Generation 
### Structure
You are writing a wikipedia article about the human gene {gene} ({get_protein_name(gene)}). Write a section of the article about structure that describes the molecular structure of the protein, including details on primary, secondary, tertiary, and quaternary structure. You may also include specific domains, prominent folds, common post translational modifications, splice variant isoforms, etc.
### Function
You are writing a wikipedia article about the human gene {gene} ({get_protein_name(gene)}). Write a section of the article about function that includes information about the function of the gene or protein in healthy human cells. Function should primarily include information about the molecular processes that the protein is involved in, its role in cell biology, and organismal outcomes of those processes. This may also include the molecular activities of an individual protein and/or information about where the protein is active in the cell.
### Interaction
You are writing a wikipedia article about the human gene {gene} ({get_protein_name(gene)}). Write a section of the article about interactions that describes any physical interactions that the subject protein participates in with other proteins or nucleic acids. These may include multiprotein complexes or more transitory interactions such as activating or inhibitory interactions.
### Clinical Significance
You are writing a wikipedia article about the human gene {gene} ({get_protein_name(gene)}). Write a section of the article about clinical Significance that describes diseases or conditions that are a result of mutations in the gene, alterations in its expression level, or alterations to its normal interactions. There is another section about function in healthy cells, so do not cover that in detail.

## Prompts - Edit Generation
### System Prompt
You are an expert biologist that is editing a Wikipedia article. Have a scholarly tone and make sure to cite your work according to the instructions.
### Completion Prompt
The following is a draft Wikipedia article for gene {gene}. Revise it to have more coherent paragraphs and a short overview section. First, write a brief overview section at the top, as you would see in a normal wikipedia article. Be careful in the overview to disinguish between the gene ({gene}) and the protein {protein_name} encoded by the gene. If applicable, categorize the protein (e.g., kinase, receptor, transmembrane) in the overview. After the overview, revise the given sections by lightly editing to organize into coherent paragraphs. Leave in the existing section heading and any formatting. Edit for clarity and coherence, removing any redundant or irrelevant sentences. However, ensure that all critical information and citations remain intact. Make sure to cite with the same paranthetical formatting as the original sections. That means that a sentence might end like this: '... the ADCK5-SOX9-PTTG1 pathway (Qiu2020aarFDC pages 3-3).' Notice that there's a space between the previous word and the citation. Do not include the '## References' section, I am going to add it myself."
The citations that you must include are:

{references}

Ensure that these citations are included in the text, and that they are formatted correctly.

[START OF ARTICLE]

{main}

[END OF ARTICLE]

Remember, all cited information is very important, removing statements with citations will cause the article to be rejected and not accepted to Wikipedia, which you do not want to happen.
