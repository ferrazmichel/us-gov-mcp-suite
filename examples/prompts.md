# Example AI Agent Prompts

Use `outputMode: "mcp_summary"` inside interactive chat sessions for fast responses and minimal token consumption.

## 1. Equity Research & SEC Filings (`sec-edgar-filings-mcp`)
> "Fetch the latest 10-K and 8-K filings for AAPL and NVDA using `mcp_summary`, and compare their audited US-GAAP Revenue, Net Income, Net Margin %, and Cash."

## 2. Importers & E-Commerce Sourcing (`usitc-hts-tariff-mcp`)
> "Calculate the total US landed cost for HTS `8507.60.00.10` on a $25,000 ocean shipment (+ $1,200 freight/insurance) and compare China vs. Vietnam vs. Mexico vs. South Korea."

## 3. CPAs, ERPs & 1099-NEC Tax Compliance (`us-1099-nec-state-compliance-mcp`)
> "Check whether a $1,250 ACH contractor payment in 2026 triggers Form 1099-NEC filing in CA, NY, TX, PA, and MA, and whether IRS CF/SF covers each state."

## 4. Healthcare, Legal & Supply Chain Recalls (`openfda-recall-device-radar`)
> "Find all ongoing Class I medical device recalls in openFDA reported since 2026-01-01 using `mcp_summary`."

## 5. Vendor Safety Due Diligence (`osha-safety-compliance-mcp`)
> "Review the last 50 DOL OSHA safety inspections and total current penalties for facilities in Texas matching 'Amazon' using `mcp_summary`."

## 6. Environmental & Real Estate ESG Screening (`epa-echo-environmental-mcp`)
> "Screen industrial facilities in Ohio flagged with Significant Non-Compliance (SNC) under the Clean Water Act using EPA ECHO."

## 7. Freight Brokers, Logistics & Insurance (`fmcsa-carrier-safety-mcp`)
> "Vet USDOT carrier safety status, operating authority, and BIPD insurance coverage for newly registered motor carriers in Texas."
