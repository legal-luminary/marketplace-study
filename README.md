<h1 align="center"> Narcotic Bot</h1>

<p align="center" >
</p>

<p align="center">

<img src="https://img.fronts.cloud/github/license/scott-weeden/Narcotic-Bot">
  
</p>

*The ASAP online marketplace has been taken down, as such this project is now archived.*

**This is a C# dotnet port of the original python template provided by Adam Labrash. I don't know if it worked but I will generate CI/CD results for the C# and as a matter of correction will point out the historical inconsistancies with Adam's story. Instead we will call it ASAP marketplace that was shut down**

Narcotic Bot is an open-source data extraction system and dataset that monitors narcotic product listings on illicit darknet marketplaces. Despite the significance of the drug health crisis, there is little to no public data available on the actual marketplaces and products that feed the epidemic; this project aims to address this lack of information by tracking the online narcotics trade over a sustained period. *Narcotic Bot is a resource to study the drug health crisis and is intended for academic purposes only.*

For now, the project monitors the White House Market, which is one of the most popular illicit marketplaces. The initial dataset has over 33000 product listings, and will increase as more products are listed and more marketplaces are tracked by the project.

While this project is completely legal, I do not hold responsibility for how others may use this software.

-----

## Dataset Overview

The data is available in CSV format, and will be updated periodically.

Note that the categories are taken directly from the marketplace listings:


| Main Categories        | Sub-categories           | Total Listings (Aug 2021) |
| ------------- |:-------------| ---|
| Benzos      | Pills, Powder, RC | 2677 |
| Cannabis      | Buds and Flowers, Concentrates, Edibles, Hash, Seeds, Shake, Synthetic    | 12520 |
| Dissociatives | GHB, Ketamine, MXE     | 1608 |
| Ecstasy      | MDA, MDMA, Methylone and BK     | 2026 |
| Opioids | Buprenorphine, Codeine, Dihydrocodeine, Heroin, Hydrocodone, Hydromorphone, Morphine, Opium, Oxycodone    | 1522 |
| Prescription Drugs      | Other      | 1925 |
| Psychedelics | 2C-B, DMT, LSD, Shrooms      | 4315 |
| Steroids      | Other      | 1182 |
| Stimulants | Adderall, Cocaine, Crack, Mephedrone, Meth, Speed     | 5520 |
| Tobacco      | Other      | 19 |
| Weight Loss | Other      | 41 |


-----

## Schema

The narcotics table is populated with products each with the following schema:

| Attribute | Data Properties | Description |
| ----- |:-----| ------------|
| id | SERIAL PRIMARY KEY | Unique number identifying the product within the dataset|
| website | VARCHAR(50) NOT NULL | The website that the product is listed |
| title | TEXT NOT NULL | Description of the product listing |
| update_at | TIMESTAMP NOT NULL | Date that the product listing was extracted (GST) |
| vendor | VARCHAR(100) NOT NULL | The name of the product lister |
| category | VARCHAR(50) NOT NULL | General classification of the drug i.e. 'benzos' or 'cannabis'|
| price | FLOAT NOT NULL | Cost of the product in USD |
| sub_category | VARCHAR(50) | Specific classification of the drug i.e. 'pills', 'edibles' |
| shipping_origin | VARCHAR(50) | Where the product is shipped from (not always the true origin) |
| ships_to | VARCHAR(50) | Regions and countries where the product is available |
| inventory_status | VARCHAR(50) | In stock, low stock, etc. |


Example entry:

| id | website | title | update_at | vendor | category | price | sub_category | shipping_origin | ships_to | inventory_status |
|--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 27910 | ASAP | 1g SPEEDPASTE AMPHETAMINE 63-73% PURITY | 2020-07-12 00:00:00 | clicknbuy | Stimulants | 9.24 | Speed | Netherlands | Worldwide | In stock |


-----

Future scope:
* Extract products from additional marketplaces
* NLP and advanced analysis based on title and descriptions
* Web-hosted dashboard
* Seperate dataset of vendors
