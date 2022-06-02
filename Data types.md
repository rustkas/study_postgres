```
                                             Список типов данных
   Схема    |             Имя             |                             Описание                              
------------+-----------------------------+-------------------------------------------------------------------
 pg_catalog | "any"                       | 
 pg_catalog | "char"                      | single character
 pg_catalog | abstime                     | absolute, limited-range date and time (Unix system time)
 pg_catalog | aclitem                     | access control list
 pg_catalog | anyarray                    | 
 pg_catalog | anyelement                  | 
 pg_catalog | anyenum                     | 
 pg_catalog | anynonarray                 | 
 pg_catalog | anyrange                    | 
 pg_catalog | bigint                      | ~18 digit integer, 8-byte storage
 pg_catalog | bit                         | fixed-length bit string
 pg_catalog | bit varying                 | variable-length bit string
 pg_catalog | boolean                     | boolean, 'true'/'false'
 pg_catalog | box                         | geometric box '(lower left,upper right)'
 pg_catalog | bytea                       | variable-length string, binary values escaped
 pg_catalog | character                   | char(length), blank-padded string, fixed storage length
 pg_catalog | character varying           | varchar(length), non-blank-padded string, variable storage length
 pg_catalog | cid                         | command identifier type, sequence in transaction id
 pg_catalog | cidr                        | network IP address/netmask, network address
 pg_catalog | circle                      | geometric circle '(center,radius)'
 pg_catalog | cstring                     | 
 pg_catalog | date                        | date
 pg_catalog | daterange                   | range of dates
 pg_catalog | double precision            | double-precision floating point number, 8-byte storage
 pg_catalog | event_trigger               | 
 pg_catalog | fdw_handler                 | 
 pg_catalog | gtsvector                   | GiST index internal text representation for text search
 pg_catalog | inet                        | IP address/netmask, host address, netmask optional
 pg_catalog | int2vector                  | array of int2, used in system tables
 pg_catalog | int4range                   | range of integers
 pg_catalog | int8range                   | range of bigints
 pg_catalog | integer                     | -2 billion to 2 billion integer, 4-byte storage
 pg_catalog | internal                    | 
 pg_catalog | interval                    | @ <number> <units>, time interval
 pg_catalog | json                        | 
 pg_catalog | jsonb                       | Binary JSON
 pg_catalog | language_handler            | 
 pg_catalog | line                        | geometric line
 pg_catalog | lseg                        | geometric line segment '(pt1,pt2)'
 pg_catalog | macaddr                     | XX:XX:XX:XX:XX:XX, MAC address
 pg_catalog | money                       | monetary amounts, $d,ddd.cc
 pg_catalog | name                        | 63-byte type for storing system identifiers
 pg_catalog | numeric                     | numeric(precision, decimal), arbitrary precision number
 pg_catalog | numrange                    | range of numerics
 pg_catalog | oid                         | object identifier(oid), maximum 4 billion
 pg_catalog | oidvector                   | array of oids, used in system tables
 pg_catalog | opaque                      | 
 pg_catalog | path                        | geometric path '(pt1,...)'
 pg_catalog | pg_ddl_command              | internal type for passing CollectedCommand
 pg_catalog | pg_lsn                      | PostgreSQL LSN datatype
 pg_catalog | pg_node_tree                | string representing an internal node tree
 pg_catalog | point                       | geometric point '(x, y)'
 pg_catalog | polygon                     | geometric polygon '(pt1,...)'
 pg_catalog | real                        | single-precision floating point number, 4-byte storage
 pg_catalog | record                      | 
 pg_catalog | refcursor                   | reference to cursor (portal name)
 pg_catalog | regclass                    | registered class
 pg_catalog | regconfig                   | registered text search configuration
 pg_catalog | regdictionary               | registered text search dictionary
 pg_catalog | regnamespace                | registered namespace
 pg_catalog | regoper                     | registered operator
 pg_catalog | regoperator                 | registered operator (with args)
 pg_catalog | regproc                     | registered procedure
 pg_catalog | regprocedure                | registered procedure (with args)
 pg_catalog | regrole                     | registered role
 pg_catalog | regtype                     | registered type
 pg_catalog | reltime                     | relative, limited-range time interval (Unix delta time)
 pg_catalog | smallint                    | -32 thousand to 32 thousand, 2-byte storage
 pg_catalog | smgr                        | storage manager
 pg_catalog | text                        | variable-length string, no limit specified
 pg_catalog | tid                         | (block, offset), physical location of tuple
 pg_catalog | time with time zone         | time of day with time zone
 pg_catalog | time without time zone      | time of day
 pg_catalog | timestamp with time zone    | date and time with time zone
 pg_catalog | timestamp without time zone | date and time
 pg_catalog | tinterval                   | (abstime,abstime), time interval
 pg_catalog | trigger                     | 
 pg_catalog | tsm_handler                 | 
 pg_catalog | tsquery                     | query representation for text search
 pg_catalog | tsrange                     | range of timestamps without time zone
 pg_catalog | tstzrange                   | range of timestamps with time zone
 pg_catalog | tsvector                    | text representation for text search
 pg_catalog | txid_snapshot               | txid snapshot
 pg_catalog | unknown                     | 
 pg_catalog | uuid                        | UUID datatype
 pg_catalog | void                        | 
 pg_catalog | xid                         | transaction id
 pg_catalog | xml                         | XML content
(88 строк)


```
