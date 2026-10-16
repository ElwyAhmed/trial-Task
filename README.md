# trial-Task
trial Task

Here is a summary of the work done so far on the Inventory Count assignment (SAP BTP ABAP Trial, RAP):

1. System setup

Created an SAP BTP trial account.
Created the ABAP trial instance in the trial subaccount (Instances and Subscriptions).
Created a service key for the instance.
In Eclipse (ADT), created an ABAP Cloud Project using the service key, and created the package ZTECHNICALTRIALTASK

2. Database tables

ZHEADER_STORE: count document header (ID, store, count date, status, created by/at).
ZITEM_STORE: count items (article, book quantity, counted quantity, unit, difference, counted flag), linked to the header by ID.
ZARTICLE_STORE: article master data with book stock per store.

3. CDS data model

ZDDHEADER_STORE: root interface view on the header table.
ZDDITEM_STORE: item interface view with a parent association to the header and a criticality field for the difference (red = shortage, yellow = surplus, green = no difference).

4. Projection views (UI layer)

ZBUILD_HEADER_STORE: header projection with UI annotations (list columns, Store and Status filters, General Information section on the Object Page).
ZBUILD_ITEM_STORE: item projection, redirected to the header projection as parent.

5. Service

Service definition ZSD_HEADER exposing Header_list and Item_list.
Service binding ZSB_STORE (OData V4 – UI), published.
Fiori Elements preview tested: the “Count Documents” List Report opens with the Store and Status filters.
