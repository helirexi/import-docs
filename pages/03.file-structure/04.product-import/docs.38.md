---
title: 'Product Import'
visible: true
---

Pacemaker Community comes with a product import and the apropriate command `import:products` therefore. You can find more information about how to invoke the command in the [Usage](/getting-started/usage) section.

In general the filename for the dedicated MSI import **MUST** match the following pattern `<PREFIX>_<FILENAME>_<COUNTER>.csv`, whereas the default `<PREFIX>` is `product-import`, the `<FILENAME>` is a combination of date and time like `20190608-114344`, and the `<COUNTER>` is a consecutive number with two digits starting with `01`. This results in a filename like `product-import_20190608-114344_01.csv`. Additionally an apropriate `.ok` file is needed.

> ATTENTION: Please be aware that the three parts **MUST** be separated with an underscore "_" as there is meaning for the bunch import behind its structure.

### Unique Identifier

The unique identifier for the product import is the SKU. The SKU is a mandatory field that has be available in the column `sku` on **EVERY** row of the CSV file.

### Compatibility & Extensions

The structure for the Product import is nearly 100 % compatible with the Magento 2 CSV structure. Have a look at the Magento 2 [documentation](http://docs.magento.com/m2/ce/user_guide/system/data-attributes-product.html) for a detailed description of the CSV file structure.

Especially for the product import, Magento extends the default CSV format for some special cases called complex data, which provides some kind of data serialization to extend the default CSV format. Magento describes this on a dedicated [page](https://docs.magento.com/m2/ce/user_guide/system/data-complex.html) on their website. Beside the topics that has been described on that page by Magento itself, there is a column with additional attributes that also uses a complex data format like [Additional Attributes](/file-structure/product-import/additional-attributes).

In addition to the Magento 2 CSV structure, it is possible to add additional columns to allow tier prices and MSI stock data also be part of the product import. Both columns contains serialized data like the [additional_attributes](/file-structure/product-import/additional-attributes) column does.

During product import, Pacemaker Community extracts the data from the columns and creates separate CSV files. These CSV files are 1:1 the format described for [Tier Prices](/file-structure/product-import-tier-prices) and [MSI](/file-structure/product-import-msi) import in the corresponding sections. After the products have been imported, Pacemaker Community imports the tier prices as well as the MSI data.