# Juris Data Normalization Analysis

## Introduction

The objective of this analysis on Juris data is to detect instances where case ruling metadata fields are not properly normalized. Such inconsistencies can compromise the integrity of the application, particularly when users browse case rulings via the search filters.

## How Browsing Works in Juris

Browsing in Juris primarily relies on filter textboxes located on the main page. These textboxes are connected to various metadata fields of case rulings such as the judge’s name, voting result, decision type, and procedural means. When users type into a filter textbox, suggestions are presented based on the existing data.

If this metadata is not normalized, users may not see all case rulings corresponding to a given filter value, even when they think they should. This fragmentation arises because identical concepts are represented using different formats or terms.

## Causes of Normalization Issues

These inconsistencies stem from manual data entry by various contributors, leading to variations in the way the same information is recorded since different people can use different terms when actually referring to the same matter. Below are real examples illustrating the types of issues found:

- **Typos**: `"Revita"` → `"Revista"`
- **Old Spelling Agreements**: `"Revista excepcional"` → `"Revista excecional"`
- **Capitalization**: `"DESPACHO"` → `"Despacho"`
- **Punctuation**: `"Conflito."` → `"Conflito"`
- **Rephrasing**: `"Acordão Unimizador"` → `"Acordão de unificação"`
- **Extra Spaces**

Detecting and correcting these normalization issues is key to improving search accuracy and user experience within the Juris application.

