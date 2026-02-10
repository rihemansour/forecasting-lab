# FreshRetailNet-50K

**FreshRetailNet-50K** is the first large-scale benchmark specifically designed for **censored demand estimation** in the fresh retail domain. It incorporates approximately 20% organically occurring stockout data across a diverse range of urban retail environments.

[**Technical Report**](#) | [**GitHub Repo**](#) | [**Hugging Face Dataset**](https://huggingface.co/datasets/Dingdong-Inc/FreshRetailNet-50K)

---

## 📊 Dataset Overview
The dataset comprises **50,000 store-product 90-day time series**, totaling 4.5 million training rows. It is derived from 898 stores across 18 major cities and covers 865 perishable SKUs. 

Unique to this dataset are the **hourly stock status records** and meticulous stockout event annotations, which allow researchers to move beyond traditional forecasting and delve into latent demand recovery.

### Key Features:
* **Scale:** 50k unique store-product pairs.
* **Granularity:** Hourly sales and stock status.
* **Rich Context:** Includes weather (precipitation, temperature, humidity), promotional discounts, and holiday flags.
* **Real-world Impact:** Features 20% organic stockout events to simulate real retail challenges.

---

## 📂 Data Schema

| Field | Type | Description |
| :--- | :--- | :--- |
| `city_id` | `int64` | The encoded city id |
| `store_id` | `int64` | The encoded store id |
| `management_group_id` | `int64` | The encoded management group id |
| `first_category_id` | `int64` | The encoded first category id |
| `second_category_id` | `int64` | The encoded second category id |
| `third_category_id` | `int64` | The encoded third category id |
| `product_id` | `int64` | The encoded product id |
| `dt` | `string` | The date |
| `sale_amount` | `float64` | Daily sales amount after global normalization |
| `hours_sale` | `Sequence` | Hourly sales amount after global normalization |
| `stock_hour6_22_cnt` | `int32` | Number of out-of-stock hours (6:00-22:00) |
| `hours_stock_status` | `Sequence` | Hourly out-of-stock status |
| `discount` | `float64` | Discount rate (1.0 = no discount, 0.9 = 10% off) |
| `holiday_flag` | `int32` | Holiday indicator |
| `activity_flag` | `int32` | Activity indicator |
| `precpt` | `float64` | Total precipitation |
| `avg_temperature` | `float64` | Average temperature |
| `avg_humidity` | `float64` | Average humidity |
| `avg_wind_level` | `float64` | Average wind force |

### Hierarchical Structure
* **Warehouse:** `city_id` > `store_id`
* **Product Category:** `management_group_id` > `first_category_id` > `second_category_id` > `third_category_id` > `product_id`

---

## 🚀 Getting Started

You can load the dataset using the Hugging Face `datasets` library:

```python
from datasets import load_dataset

# Load the dataset
dataset = load_dataset("Dingdong-Inc/FreshRetailNet-50K")

# Print dataset structure
print(dataset)

---

## 🎯 Intended Use
The **FreshRetailNet-50K** dataset is intended to be freely used by the research and development community to advance the state-of-the-art in:
* **Latent Demand Recovery:** Modeling true demand when historical data is "censored" by stockouts.
* **Demand Forecasting:** Improving accuracy in high-volatility fresh retail environments.

> [!IMPORTANT]
> Users are responsible for checking if the dataset license is fit for their intended purpose.

---

## 📜 Metadata & License
* **Data Developer:** Dingdong-Inc
* **Release Date:** 05/08/2025
* **Version:** 1.0 (05/08/2025)
* **License:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/legalcode)
* **Hugging Face Link:** [FreshRetailNet-50K](https://huggingface.co/datasets/Dingdong-Inc/FreshRetailNet-50K)