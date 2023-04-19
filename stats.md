
Stats:
 For every query file, respective `stats.xml` files are generated, to know the status of evey query and understand the flow of execution

    Sample `stats.xml` file:

        <?xml version="1.0" ?>
        <Session name="$global$" time_taken="747.395" uuid="7f582e62-4f7a-4054-b797-dda5b6198f86">
            <Query status="executed" time_taken="31.792" uuid="5b205c44-a639-49c2-8f98-3691ac7489d1">DROP DATABASE IF EXISTS db_jlR CASCADE</Query>
            <Query status="executed" time_taken="223.79" uuid="1832653d-99ad-49bc-a8a1-c6bc25bf7cd9">CREATE DATABASE db_jlR</Query>
            <Query status="executed" time_taken="368.746" uuid="e21b27ef-acf5-4fa8-8543-82cd96921a90">use db_jlR</Query>
            <Query status="executed" time_taken="123.063" uuid="51105d33-3b72-41e5-aca2-87d82e28f6a8">CREATE TABLE hijk</Query>
        </Session>