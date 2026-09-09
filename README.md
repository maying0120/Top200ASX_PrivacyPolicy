# Top200ASX Privacy Policy Dataset

This repository contains a dataset of public privacy-policy and AI-related disclosure pages collected from the top 200 ASX-listed companies. The dataset was prepared for research on how large Australian-listed companies publicly disclose AI-related or automated-decision-making practices.

## Files

### `asx200_policy_page_corpus.csv`

Main corpus file. It contains 219 page-level records:

- 200 `privacy_policy` records, one for each ASX 200 company in the sampled company list.
- 19 `ai_policy` records for companies with a validated standalone AI-related disclosure page.

The corpus includes page URLs, crawl timestamps, extracted page text, cleaned privacy-policy text where available, and binary indicators for whether AI-related disclosure was found.

### `asx200_validated_ai_disclosures.csv`

Validated disclosure list. It contains 60 disclosure-level records across 51 unique companies:

- 41 `privacy_policy` disclosure records.
- 19 `ai_policy` disclosure records.
- 9 companies appear in both disclosure surfaces.
- 32 companies appear only with a privacy-policy disclosure.
- 10 companies appear only with a standalone AI-related disclosure.

The first nine columns are the intended data fields. Any trailing blank columns are empty export artifacts and can be ignored.

## Data Dictionary

### Main Corpus Columns

| Column | Description |
| --- | --- |
| `ticker` | ASX ticker code for the company. |
| `company_name` | Company name. |
| `entity_type` | Entity source/type. In this dataset, records are ASX-listed companies. |
| `gics_sector` | GICS sector assigned to the company. |
| `industry_group` | GICS industry group assigned to the company. |
| `company_domain` | Main company domain used during collection. |
| `page_type` | Type of page represented by the row: `privacy_policy` or `ai_policy`. |
| `page_url` | URL of the collected policy or disclosure page. |
| `clean_word_count` | Word count after cleaning, where text was available. |
| `crawl_timestamp` | Timestamp for the crawl or page-text collection. |
| `crawled_page_text` | Raw extracted text from the crawled page. |
| `cleaned_privacy_policy_text` | Cleaned privacy-policy text used for analysis, where applicable. |
| `privacy_policy_not_found_label` | Indicates privacy-policy collection issues, such as `not found` or `no text`. Blank means no such issue was recorded. |
| `ai_policy_page_found` | Indicates whether a standalone AI-related policy/disclosure page was found for the company. |
| `privacy_policy_ai_disclosure` | Indicates whether a validated AI-related disclosure was found within the privacy policy. This field applies to `privacy_policy` rows. |

### Validated Disclosure List Columns

| Column | Description |
| --- | --- |
| `anonymous_company_id` | Anonymous company identifier assigned for reporting, such as `C1`, `C2`, and so on. The same company keeps the same ID across multiple disclosure records. |
| `ticker` | ASX ticker code for the company. |
| `company_name` | Company name. |
| `entity_type` | Entity source/type. |
| `gics_sector` | GICS sector assigned to the company. |
| `industry_group` | GICS industry group assigned to the company. |
| `company_domain` | Main company domain. |
| `disclosure_page_url` | URL of the validated disclosure page. |
| `disclosure_page_type` | Disclosure surface: `privacy_policy` or `ai_policy`. |

## Summary Statistics

For the 200 companies in the corpus:

- 41 companies had a validated AI-related disclosure within their privacy policy.
- 19 companies had a validated standalone AI-related disclosure page.
- 9 companies had both disclosure types.
- 51 companies had at least one of the two disclosure types.
- 149 companies had neither disclosure type in the collected corpus.

Privacy-policy collection status:

- 194 privacy-policy pages had collected text.
- 5 companies were marked as `not found` for privacy-policy collection.
- 1 company was marked as `no text`.

## Notes on Use

- Rows in `asx200_policy_page_corpus.csv` are page-level records, not company-level records. A company can appear more than once if it has both a privacy-policy row and a standalone AI-policy row.
- Rows in `asx200_validated_ai_disclosures.csv` are validated disclosure records. A company can appear twice if it has both `privacy_policy` and `ai_policy` disclosure surfaces.
- `privacy_policy_ai_disclosure` should be interpreted for privacy-policy rows. It is blank for standalone `ai_policy` rows.
- `ai_policy_page_found` identifies whether a standalone AI-related disclosure page was found during validation.
- The text fields may contain long policy text and website navigation text produced during page extraction. Downstream analyses should use the cleaned text field where available.

## Suggested Citation

If using this dataset, cite the associated paper or project that introduced the dataset. If no formal citation is available, cite this repository and include the dataset filename and access date.

## License

No license is specified in this repository. Please contact the dataset creator before redistributing or reusing the dataset beyond the associated research purpose.
