[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fvercel%2Fvercel%2Ftree%2Fmain%2Fexamples%2Fflask&demo-title=Flask%20API&demo-description=Use%20Flask%20API%20on%20Vercel%20with%20Serverless%20Functions%20using%20the%20Python%20Runtime.&demo-url=https%3A%2F%2Fvercel-plus-flask.vercel.app%2F&demo-image=https://assets.vercel.com/image/upload/v1669994600/random/python.png)

# Flask + Vercel

This example shows how to use Flask on Vercel with Serverless Functions using the [Python Runtime](https://vercel.com/docs/concepts/functions/serverless-functions/runtimes/python).

## Demo

https://vercel-plus-flask.vercel.app/

## How it Works

This example uses the Web Server Gateway Interface (WSGI) with Flask to handle requests on Vercel with Serverless Functions.

## Running Locally


npm i -g vercel
python -m venv .venv
source .venv/bin/activate
uv sync  # or alternatively pip install flask gunicorn
gunicorn main:app


Your Flask application is now available at `http://localhost:3000`.

## System Architecture Diagram


flowchart TD

subgraph group_storefront["Customer storefront"]
  node_catalog["Product catalog<br/>[app.py]"]
  node_search["Search and filtering<br/>[app.py]"]
  node_product_detail["Product details<br/>[app.py]"]
  node_templates["Jinja templates"]
end

subgraph group_identity["Accounts and access"]
  node_accounts["Registration and login<br/>[app.py]"]
  node_profiles["User profiles<br/>[app.py]"]
end

subgraph group_commerce["Commerce operations"]
  node_cart["Shopping cart<br/>[app.py]"]
  node_checkout["Order placement<br/>[app.py]"]
  node_database_setup["Schema and sample data<br/>[init_db.py]"]
  node_database[("SQLite database<br/>[database.db]")]
end

subgraph group_admin["Administration"]
  node_order_management["Order management<br/>[app.py]"]
  node_product_management["Product management<br/>[app.py]"]
  node_customer_management["Customer management<br/>[app.py]"]
  node_image_uploads["Product image uploads<br/>[app.py]"]
end

node_customer(("Customer"))
node_administrator(("Administrator"))
node_flask_app["Flask application<br/>[app.py]"]

node_customer -->|"uses storefront"| node_flask_app
node_administrator -->|"uses admin"| node_flask_app
node_flask_app -->|"handles accounts"| node_accounts
node_flask_app -->|"manages profiles"| node_profiles
node_flask_app -->|"lists products"| node_catalog
node_flask_app -->|"searches products"| node_search
node_flask_app -->|"shows details"| node_product_detail
node_flask_app -->|"adds to cart"| node_cart
node_flask_app -->|"places orders"| node_checkout
node_flask_app -->|"manages orders"| node_order_management
node_flask_app -->|"manages products"| node_product_management
node_flask_app -->|"manages customers"| node_customer_management
node_flask_app -->|"uploads images"| node_image_uploads
node_flask_app -->|"renders pages"| node_templates
node_database_setup -->|"creates and seeds"| node_database
node_flask_app -.->|"reads and writes"| node_database

click node_flask_app "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_accounts "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_profiles "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_catalog "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_search "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_product_detail "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_cart "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_checkout "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_order_management "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_product_management "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_customer_management "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_image_uploads "https://github.com/yongnaykhouch/kk/blob/main/app.py"
click node_templates "https://github.com/yongnaykhouch/kk/tree/main/templates"
click node_database_setup "https://github.com/yongnaykhouch/kk/blob/main/init_db.py"
click node_database "https://github.com/yongnaykhouch/kk/blob/main/database.db"

classDef toneNeutral fill:#f8fafc,stroke:#334155,stroke-width:1.5px,color:#0f172a
classDef toneBlue fill:#dbeafe,stroke:#2563eb,stroke-width:1.5px,color:#172554
classDef toneAmber fill:#fef3c7,stroke:#d97706,stroke-width:1.5px,color:#78350f
classDef toneMint fill:#dcfce7,stroke:#16a34a,stroke-width:1.5px,color:#14532d
classDef toneRose fill:#ffe4e6,stroke:#e11d48,stroke-width:1.5px,color:#881337
classDef toneIndigo fill:#e0e7ff,stroke:#4f46e5,stroke-width:1.5px,color:#312e81
classDef toneTeal fill:#ccfbf1,stroke:#0f766e,stroke-width:1.5px,color:#134e4a
class node_catalog,node_search,node_product_detail,node_templates toneBlue
class node_accounts,node_profiles toneAmber
class node_cart,node_checkout,node_database_setup,node_database toneMint
class node_order_management,node_product_management,node_customer_management,node_image_uploads toneRose
class node_customer,node_administrator toneIndigo
class node_flask_app toneTeal


Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=vercel-examples):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fvercel%2Fvercel%2Ftree%2Fmain%2Fexamples%2Fflask&demo-title=Flask%20API&demo-description=Use%20Flask%20API%20on%20Vercel%20with%20Serverless%20Functions%20using%20the%20Python%20Runtime.&demo-url=https%3A%2F%2Fvercel-plus-flask.vercel.app%2F&demo-image=https://assets.vercel.com/image/upload/v1669994600/random/python.png)
