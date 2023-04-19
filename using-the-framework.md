
- Query:
  every query must start with the query prefix(`>>>`) and end with a semicolon(`;`)

        >>> query;
- Output:
  the expected output is to be written between the output prefix (`====`)

        ====
        output
         ...
        ====

- Matcher:
    Defines how to match the expected output with the actual output from query. 
  
      !!! match matcher_type

    Types:
  - SuccessMatcher
  - RowsOrderedMatcher
  - RowsUnorderedMatcher
  - RowsRegexOrderedMatcher
  - RowsRegexUnorderedMatcher
  - ErrorContainsMatcher
  - ErrorIgnoreMatcher
  - ErrorRegexMatcher

- Session:

        <> SESSION BEGIN session_name
        query
        query
         ...
        <> SESSION END
- Session groups:
 Runs multiple sessions concurrently

      <> SESSION RUN session_name1, session_name2, ...



- Comments:

      -- This is a comment

- Sleep:

        <> SLEEP number_of_seconds
- UDF:
 User Defined Function, the user defines a function, than can be used while running the query file.

      <> UDF (file_path, function_name, arguments)


- Functions:
    
      func(function_name, args)
- Logs: Logs are generated for every query file and stored in individual log files under the folder **usqle_logs**, they also appear in the console and are stored together in main.log file.

    Sample logs:
  
        2023-04-17 12:28:07,774-INFO - Starting session($global$:7f582e62-4f7a-4054-b797-dda5b6198f86 using connection b20e5e2c-0e54-484d-b5fe-97edcb972cb9
        2023-04-17 12:28:07,774-INFO - Starting query:5b205c44-a639-49c2-8f98-3691ac7489d1: DROP DATABASE IF EXISTS db_jlR CASCADE
        2023-04-17 12:28:39,567-INFO - Finished query:5b205c44-a639-49c2-8f98-3691ac7489d1. Time Taken: 31.792
        2023-04-17 12:28:39,567-INFO - Starting query:1832653d-99ad-49bc-a8a1-c6bc25bf7cd9: CREATE DATABASE db_jlR
        2023-04-17 12:32:23,358-INFO - Finished query:1832653d-99ad-49bc-a8a1-c6bc25bf7cd9. Time Taken: 223.79
        2023-04-17 12:32:23,358-INFO - Starting query:e21b27ef-acf5-4fa8-8543-82cd96921a90: use db_jlR
        2023-04-17 12:38:32,105-INFO - Finished query:e21b27ef-acf5-4fa8-8543-82cd96921a90. Time Taken: 368.746
        2023-04-17 12:38:32,105-INFO - Starting query:51105d33-3b72-41e5-aca2-87d82e28f6a8: CREATE TABLE hijk
        2023-04-17 12:40:35,169-INFO - Finished query:51105d33-3b72-41e5-aca2-87d82e28f6a8. Time Taken: 123.063
        2023-04-17 12:42:37,790-INFO - Ending session($global$:7f582e62-4f7a-4054-b797-dda5b6198f86. Time Taken: 747.395


- Stats:
 For every query file, respective `stats.xml` files are generated, to know the status of evey query and understand the flow of execution

    Sample `stats.xml` file:

        <?xml version="1.0" ?>
        <Session name="$global$" time_taken="747.395" uuid="7f582e62-4f7a-4054-b797-dda5b6198f86">
            <Query status="executed" time_taken="31.792" uuid="5b205c44-a639-49c2-8f98-3691ac7489d1">DROP DATABASE IF EXISTS db_jlR CASCADE</Query>
            <Query status="executed" time_taken="223.79" uuid="1832653d-99ad-49bc-a8a1-c6bc25bf7cd9">CREATE DATABASE db_jlR</Query>
            <Query status="executed" time_taken="368.746" uuid="e21b27ef-acf5-4fa8-8543-82cd96921a90">use db_jlR</Query>
            <Query status="executed" time_taken="123.063" uuid="51105d33-3b72-41e5-aca2-87d82e28f6a8">CREATE TABLE hijk</Query>
        </Session>


- Benchmark file:
 When the expected output is stored in an external file, the file or folder location should be provided to check if the actual output is same as the expected output.

        !!! benchmark benchmark_file_location
