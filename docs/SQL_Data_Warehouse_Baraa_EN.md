# SQL Data Warehouse from Scratch | Full Hands-On Data Engineering Project

| Time | Subtitle |
|------|----------|
| 0s | hey friends so today we are diving into something very exciting Building |
| 4s | Together modern SQL data warehouse projects but this one is not any project |
| 9s | this one is a special one not only you will learn how to build a modern Data |
| 13s | Warehouse from the scratch but also you will learn how I implement this kind of |
| 17s | projects in Real World Companies I'm bar zini and I have built more than five |
| 22s | successful data warehouse projects in different companies and right now I'm |
| 26s | leading big data and Pi Projects at Mercedes-Benz so that's me I'm sharing |
| 30s | with you real skills real Knowledge from complex projects and here's what you |
| 35s | will get out of this project as a data architect we will be designing a modern |
| 39s | data architecture following the best practices and as a data engineer you |
| 43s | will be writing your codes to clean transform load and prepare the data for |
| 48s | analyzis and as a data Modell you will learn the basics of data moding and we |
| 54s | will be creating from the scratch a new data model for analyzes and my friends |
| 58s | by the end of this project you will have a professional portfolio project to |
| 1:03 | Showcase your new skills for example on LinkedIn so feel free to take the |
| 1:07 | project modify it and as well share it with others but it going to mean the |
| 1:11 | work for me if you share my content and guess what everything is for free so |
| 1:16 | there are no hidden costs at all and in this project we will be using SQL server |
| 1:21 | but if you prefer other databases like my SQL or bis don't worry you can follow |
| 1:25 | along just fine |
| 1:31 | all right my friends so now if you want to do data analytics projects using SQL |
| 1:35 | we have three different types the first type of projects you can do data |
| 1:38 | warehousing it's all about how to organize structure and prepare your data |
| 1:43 | for data analysis it is the foundations of any data analytics projects and in |
| 1:48 | The Next Step you can do exploratory data analyzes Eda and all what you have |
| 1:52 | to do is to understand and cover insights about our data sets in this |
| 1:56 | kind of project you can learn how to ask the right questions and how to find the |
| 2:01 | answer using SQL by just using basic SQL skills now moving on to the last stage |
| 2:06 | where you can do Advanced analytics projects where you going to use Advanced |
| 2:10 | SQL techniques in order to answer business questions like finding Trends |
| 2:14 | over time comparing the performance segmenting your data into different |
| 2:18 | sections and as well generate reports for your stack holders so here you will |
| 2:22 | be solving real business questions using Advanced SQL techniques now what we're |
| 2:27 | going to do we're going to start with the first type of projects SQL data |
| 2:30 | warehousing where you will gain the following skills so first you will learn |
| 2:33 | how to do ETL elt processing using SQL in order to prepare the data you will |
| 2:38 | learn as well how to build data architecture how to do data Integrations |
| 2:42 | where we can merge multiple sources together and as well how to do data load |
| 2:45 | and data modeling so if I got you interested grab your coffee and let's |
| 2:49 | jump to the |
| 2:53 | projects all right my friends so now before we Deep dive into the tools and |
| 2:57 | the cool stuff we have first to have good understanding about what is exactly |
| 3:01 | a data warehouse why the companies try to build such a data management system |
| 3:06 | so now the question is what is a data warehouse I will just use the definition |
| 3:10 | of the father of the data warehouse Bill Inon a data warehouse is subject |
| 3:14 | oriented integrated time variance and nonvolatile collection of data designed |
| 3:20 | to support the Management's decision-making process okay I I know |
| 3:23 | that might be confusing subject oriented it means thata Warehouse is always |
| 3:27 | focused on a business area like the sales customers finance and so on |
| 3:32 | integrated because it goes and integrate multiple Source systems usually you |
| 3:36 | build a warehouse not only for one source but for multiple sources time |
| 3:40 | variance it means you can keep historical data inside the data |
| 3:43 | warehouse nonvolatile it means once the data enter the data warehouse it is not |
| 3:48 | deleted or modified so this is how build and mod defined data warehouse okay so |
| 3:53 | now I'm going to show you the scenario where your company don't have a real |
| 3:56 | data management so now let's say that you have one system and you have like |
| 4:00 | one data analyst has to go to this system and start collecting and |
| 4:03 | extracting the data and then he going to spend days and sometimes weeks |
| 4:07 | transforming the row data into something meaningful then once they have the |
| 4:12 | report they're going to go and share it and this data analyst is sharing the |
| 4:15 | report using an Excel and then you have like another source of data and you have |
| 4:20 | another data analyst that she is doing maybe the same steps collecting the data |
| 4:24 | spending a lot of time transforming the data and then share at the end like a |
| 4:28 | report and this time she is sharing the data using PowerPoint and a third system |
| 4:32 | and the same story but this time he is sharing the data using maybe powerbi so |
| 4:37 | now if the company works like this then there is a lot of issues first this |
| 4:41 | process it take too way long I saw a lot of scenarios where sometimes it takes |
| 4:46 | weeks and even months until the employee manually generating those reports and of |
| 4:50 | course what going to happen for the users they are consuming multiple |
| 4:54 | reports with multiple state of the data one report is 40 days old another one 10 |
| 4:59 | days and a third one is like 5 days so it's going to be really hard to make a |
| 5:03 | real decision based on this structure a manual process is always slow and |
| 5:08 | stressful and the more employees you involved in the process the more you |
| 5:11 | open the door for human errors and errors of course in reports leads to bad |
| 5:16 | decisions and another issue of course is handling the Big Data if one of your |
| 5:21 | sources generating like massive amount of data then the data analyst going to |
| 5:25 | struggle collecting the data and maybe in some scenarios it will not be any |
| 5:29 | more possible to get the data so the whole process can breaks and you cannot |
| 5:33 | generate any more fresh data for specific reports and one last very big |
| 5:38 | issue with that if one of your stack holders asks for an integrated report |
| 5:43 | from multiple sources well good luck with that because merging all those data |
| 5:47 | manually is very chaotic timec consuming and full of risk so this is just a |
| 5:52 | picture if a company is working without a proper data management without a data |
| 5:57 | leak data warehouse data leak houses so in order to make real and good decisions |
| 6:02 | you need data management so now let's talk about the scenario of a data |
| 6:06 | warehouse so the first thing that can happen is that you will not have your |
| 6:10 | data team collecting manually the data you're going to have a very important |
| 6:14 | component called ETL ETL stands for extract transform and load it is a |
| 6:20 | process that you do in order to extract the data from the sources and then apply |
| 6:24 | multiple Transformations on those sources and at the end it loads the data |
| 6:28 | to the data warehouse and this one going to be the single point of Truth for |
| 6:32 | analyzes and Reporting and it is called Data Warehouse so now what can happen |
| 6:37 | all your reports going to be consuming this single point of Truth so with that |
| 6:42 | you create your multiple reports and as well you can create integrated reports |
| 6:47 | from multiple sources not only from one single source so now by looking to the |
| 6:51 | right side it looks already organized right and the whole process is |
| 6:55 | completely automated there is no more manual steps which of course it ru uses |
| 7:00 | the human error and as well it is pretty fast so usually you can load the data |
| 7:04 | from the sources until the reports in matter of hours or sometimes in minutes |
| 7:09 | so there is no need to wait like weeks and months in order to refresh anything |
| 7:14 | and of course the big Advantage is that the data warehouse itself it is |
| 7:18 | completely integrated so that means it goes and bring all those sources |
| 7:22 | together in one place which makes it really easier for reporting and not only |
| 7:27 | integrate you can build in the data warehouse as well history so we have now |
| 7:31 | the possibility to access historical data and what is also amazing that all |
| 7:36 | those reports having the same data status so all those reports can have the |
| 7:40 | same status maybe sometimes one day old or something and of course if you have a |
| 7:44 | modern Data Warehouse in Cloud platforms you can really easily handle any big |
| 7:49 | data sources so no need to panic if one of your sources is delivering massive |
| 7:54 | amount of data and of course in order to build the data warehouse you need |
| 7:57 | different types of Developers so usually the one that builds the ATL component |
| 8:02 | and the data warehouse is the data engineer so they are the one that is |
| 8:07 | accessing the sources scripting the atls and building the database for the data |
| 8:11 | warehouse and now for the other part the one that is responsible for that is the |
| 8:16 | data analyst they are the one that is consuming the data warehouse building |
| 8:20 | different data models and reports and sharing it with the stack holders so |
| 8:25 | they are usually contacting the stack holders understanding the requirements |
| 8:28 | and building multiple reports based on the data warehouse so now if you have a |
| 8:32 | look to those two scenarios this is exactly why we need data management your |
| 8:37 | data team is not wasting time and fighting with the data they are now more |
| 8:42 | organized and more focused and with like data warehouse and you are delivering |
| 8:47 | professional and fresh reports that your company can count on in order to make |
| 8:52 | good and fast decisions so this is why you need a data management like a data |
| 8:57 | warehouse think about data warehouse as a busy restaurant every day different |
| 9:01 | suppliers bring in fresh ingredients vegetables spices meat you name it they |
| 9:06 | don't just use it immediately and throw everything in one pot right they clean |
| 9:10 | it shop it and organize everything and store each ingredients in the right |
| 9:15 | place fridge or freezer so this is the preparing face and when the order comes |
| 9:20 | in they quickly grab the prepared ingredients and create a perfect dish |
| 9:25 | and then serve it to the customers of the restaurant and this process is |
| 9:28 | exactly like the data warehouse process it is like the kitchen where the raw |
| 9:32 | ingredients your data are cleaned sorted and stored and when you need a report or |
| 9:37 | analyzes it is ready to serve up exactly like what you |
| 9:44 | need okay so now we're going to zoom in and focus on the component ETL if you |
| 9:49 | are building such a project you're going to spend almost 90% just building this |
| 9:53 | component the ATL so it is the core element of the data warehouse and I want |
| 9:58 | you to have a clear understanding what is exactly an ETL so our data exist in a |
| 10:04 | source system and now what we want to do is is to get our data from the source |
| 10:08 | and move it to the Target source and Target could be like database tables so |
| 10:12 | now the first step that we have to do is to specify which data we have to load |
| 10:17 | from the source of course we can say that we want to load everything but |
| 10:20 | let's say that we are doing incremental loads so we're going to go and specify a |
| 10:24 | subset of the data from The Source in order to prepare it and load it later to |
| 10:28 | the Target so this step in the ATL process we call it extract we are just |
| 10:32 | identifying the data that we need we pull it out and we don't change anything |
| 10:37 | it's going to be like one to one like the source system so the extract has |
| 10:41 | only one task to identify the data that you have to pull out from the source and |
| 10:46 | to not change anything so we will not manipulate the data at all it can stay |
| 10:50 | as it is so this is the first step in the ETL process the extracts now moving |
| 10:55 | on to the stage number two we're going to take this extract data and we will do |
| 10:59 | some manipulations Transformations and we're going to |
| 11:02 | change the shape of those data and this process is really heavy working we can |
| 11:07 | do a lot of stuff like data cleansing data integration and a lot of formatting |
| 11:12 | and data normalizations so a lot of stuff we can do in this step so this is |
| 11:16 | the second step in the ETL process the transformation we're going to take the |
| 11:20 | original data and reshape it transformat into exactly the format that we need |
| 11:26 | into a new format and shapes that we need for anal and Reporting now finally |
| 11:30 | we get to the last step in the ATL process we have the load so in this step |
| 11:35 | we're going to take this new data and we're going to insert it into the |
| 11:38 | targets so it is very simple we're going to take this prepared data from the |
| 11:42 | transformation step and we're going to move it into its final destination the |
| 11:46 | target like for example data warehouse so that's ETL in the nutshell first |
| 11:51 | extract the row data then transform it into something meaningful and finally |
| 11:55 | load it to a Target where it's going to make a difference so that's that's it |
| 11:59 | this is what we mean with the ETL process now in real projects we don't |
| 12:03 | have like only source and targets our thata architecture going to have like |
| 12:07 | multiple layers depend on your design whether you are building a warehouse or |
| 12:11 | a data lake or a data warehouse and usually there are like different ways on |
| 12:15 | how to load the data between all those layers and in order now to load the data |
| 12:19 | from one layer to another one there are like multiple ways on how to use the ATL |
| 12:24 | process so usually if you are loading the data from the source to the layer |
| 12:27 | number one like only the data from the source and load it directly to the layer |
| 12:32 | number one without doing any Transformations because I want to see |
| 12:35 | the data as it is in the first layer and now between the layer number one and the |
| 12:40 | layer number two you might go and use the full ETL so we're going to extract |
| 12:44 | from the layer one transform it and then load it to the layer number two so with |
| 12:49 | that we are using the whole process the ATL and now between Layer Two and layer |
| 12:53 | three we can do only transformation and then load so we don't have to deal with |
| 12:57 | how to extract the data because it is maybe using the same technology and we |
| 13:01 | are taking all data from Layer Two to layer three so we transform the whole |
| 13:05 | layer two and then load it to layer three and now between three and four you |
| 13:10 | can use only the L so maybe it's something like duplicating and |
| 13:13 | replicating the data and then you are doing the transformation so you load to |
| 13:18 | the new layer and then transform it of course this is not a real scenario I'm |
| 13:22 | just showing you that in order to move from source to a Target you don't have |
| 13:26 | always to use a complete ETL depend on the design of your data architecture you |
| 13:31 | might use only few components from the ETL okay so this is how ETL looks like |
| 13:36 | in real projects okay so now I would like to show you an overview of the |
| 13:40 | different techniques and methods in the etls we have wide range of possibilities |
| 13:45 | where you have to make decisions on which one you want to apply to your |
| 13:48 | projects so let's start first with the extraction the first thing that I want |
| 13:52 | to show you is we have different methods of extraction either you are going to |
| 13:56 | The Source system and pulling the data from the source or the source system is |
| 14:00 | pushing the data to the data warehouse so those are the two main methods on how |
| 14:04 | to extract data and then we have in the extraction two types we have a full |
| 14:09 | extraction everything all the records from tables and every day we load all |
| 14:13 | the data to the data warehouse or we make more smarter one where we say we're |
| 14:17 | going to do an incremental extraction where every day we're going to identify |
| 14:21 | only the new changing data so we don't have to load the whole thing only the |
| 14:25 | new data we go extract it and then load it to the data warehouse and in data |
| 14:29 | extraction we have different techniques the first one is like manually where |
| 14:33 | someone has to access a source system and extract the data manually or we |
| 14:37 | connect ourself to a database and we have then a query in order to extract |
| 14:41 | the data or we have a file that we have to pass it to the data warehouse or |
| 14:45 | another technique is to connect ourself to API and do their cods in order to |
| 14:50 | extract the data or if the data is available in streaming like in kfka we |
| 14:54 | can do event based streaming in order to extract the data another way is to use |
| 14:59 | the change data capture CDC is as well something very similar to streaming or |
| 15:04 | another way is by using web scrapping where you have a code that going to run |
| 15:08 | and extract all the informations from the web so those are the different |
| 15:11 | techniques and types that we have in the extraction now if you are talking on the |
| 15:16 | transformation there are wide range of different Transformations that we can do |
| 15:20 | on our data like for example doing data enrichment where we add values to our |
| 15:25 | data sets or we do a data integration where we have multiple sources and we |
| 15:29 | bring everything to one data model or we derive a new of columns based on already |
| 15:34 | existing one another type of data Transformations we have the data |
| 15:37 | normalization so the sources has values that are like a code and you go and map |
| 15:42 | it to more friendly values for the analyzers which is more easier to |
| 15:47 | understand and to use another Transformations we have the business |
| 15:50 | rules and logic depend on the business you can Define different criterias in |
| 15:54 | order to build like new columns and what belongs to Transformations is the data |
| 15:59 | aggregation so here we aggregate the data to a different granularity and then |
| 16:03 | we have type of transformation called Data cleansing there are many different |
| 16:07 | ways on how to clean our data for example removing the duplicates doing |
| 16:11 | data filtering handling the missing data handling invalid values or removing |
| 16:16 | unwanted spaces casting the data types and detecting the outliers and many more |
| 16:22 | so we have different types of data cleansing that we can do in our data |
| 16:26 | warehouse and this is very important transformation so as you can see we have |
| 16:30 | different types of Transformations that we can do in our data warehouse now |
| 16:34 | moving on to the load so what do we have over here we have different processing |
| 16:39 | types so either we are doing patch processing or stream processing patch |
| 16:43 | processing means we are loading the data warehouse in one big patch of data |
| 16:48 | that's going to run and load the data warehouse so it is only one time job in |
| 16:52 | order to refresh the content of the data warehouse and as well the reports so |
| 16:56 | that means we are scheduling the data warehouse in order to load it in the day |
| 17:00 | once or twice and the other type we have the stream processing so this means if |
| 17:04 | there is like a change in the source system we going to process this change |
| 17:08 | as soon as possible so we're going to process it through all the layers of the |
| 17:11 | data warehouse once something changes from The Source system so we are |
| 17:15 | streaming the data in order to have real time data warehouse which is very |
| 17:20 | challenging things to do in data warehousing and if you are talking about |
| 17:23 | the loads we have two methods either we are doing a full load or incremental |
| 17:28 | load it's a same thing as extraction right so for the full load in databases |
| 17:32 | there are like different methods on how to do it like for example we trate and |
| 17:36 | then insert that means we make the table completely empty and then we insert |
| 17:40 | everything from the scratch or another one you are doing an update insert we |
| 17:44 | call it upsert so we can go and update all the records and then insert the new |
| 17:49 | one and another way is to drop create an insert so that means we drop the whole |
| 17:53 | table and then we create it from scratch and then we insert the data it is very |
| 17:57 | similar to the truncate but here we are as well removing and drubbing the whole |
| 18:01 | table so those are the different methods of full loads the incremental load we |
| 18:05 | can use as well the upserts so update and inserts so we're going to do an |
| 18:09 | update or insert statements to our tables or if the source is something |
| 18:13 | like a log we can do only inserts so we can go and Abend the data always to the |
| 18:18 | table without having to update anything another way to do incremental load is to |
| 18:22 | do a merge and here it is very similar to the upsert but as well with a delete |
| 18:26 | so update insert delete so those are the different methods on how to load the |
| 18:30 | data to your tables and one more thing in data warehousing we have something |
| 18:34 | called slowly changing Dimensions so here it's all about the hyz of your |
| 18:39 | table and there are many different ways on how to handle the Hyer in your table |
| 18:44 | the first type is sd0 we say there is no historization and nothing should be |
| 18:48 | changed at all so that means you are not going to update anything the second one |
| 18:52 | which is more famous it is the sd1 you are doing an override so that means you |
| 18:58 | are updating the records with the new informations from The Source system by |
| 19:02 | overwriting the old value so we are doing something like the upsert so |
| 19:05 | update and insert but you are losing of course history another one we have the |
| 19:09 | scd2 and here you want to add historization to your table so what we |
| 19:13 | do so what we do each change that we get from The Source system that means we are |
| 19:18 | inserting new records and we are not going to overwrite or delete the old |
| 19:22 | data we are just going to make it inactive and the new record going to be |
| 19:26 | active one so there are different methods on how to do historization as |
| 19:30 | well while you are loading the data to the data warehouse all right so those |
| 19:34 | are the different types and techniques that you might encounter in data |
| 19:38 | management projects so now what I'm going to show you quickly which of those |
| 19:41 | types we will be using in our projects so now if we are talking about the |
| 19:44 | extraction over here we will be doing a pull extraction and about the full or |
| 19:49 | incremental it's going to be a full extraction and about the technique we |
| 19:53 | are going to be passsing files to the data warehouse and now about the data |
| 19:57 | transformation well this one we will cover everything all those types of |
| 20:02 | Transformations that I'm showing you now is going to be part of the project |
| 20:06 | because I believe in each data project you will be facing those Transformations |
| 20:10 | now if we have a look to the load our project going to be patch processing and |
| 20:14 | about the load methods we will be doing a full load since we have full |
| 20:18 | extraction and it's going to be trunk it and inserts and now about the |
| 20:22 | historization we will be doing the sd1 so that means we will be updating the |
| 20:28 | content of the thata Warehouse so those are the different techniques and types |
| 20:31 | that we will be using in our ETL process for this project all right so with that |
| 20:36 | we have now clear understanding what is a data warehouse and we are done with |
| 20:39 | the theory parts so now the next step we're going to start with the projects |
| 20:43 | the first thing that you have to do is to prepare our environment to develop |
| 20:47 | the projects so let's start with |
| 20:52 | that all right so now we go to the link in the description and from there we're |
| 20:57 | going to go to the downloads and and here you can find all the materials of |
| 21:00 | all courses and projects but the one that we need now is the SQL data |
| 21:03 | warehouse projects so let's go to the link and here we have bunch of links |
| 21:07 | that we need for the projects but the most important one to get all data and |
| 21:11 | files is this one download all project files so let's go and do that and after |
| 21:16 | you do that you're going to get a zip file where you have there a lot of stuff |
| 21:20 | so let's go and extract it and now inside it if you go over here you will |
| 21:24 | find the reposter structure from git and the most important one here is the data |
| 21:28 | ass sets so you have two sources the CRM and the Erp and in each one of them |
| 21:33 | there are three CSV files so those are the data set for the project for the |
| 21:38 | other stuffs don't worry about it we will be explaining that during the |
| 21:41 | project so go and get the data and put it somewhere at your PC where you don't |
| 21:45 | lose it okay so now what else do we have we have here a link to the get |
| 21:49 | repository so this is the link to my repository that I have created through |
| 21:53 | the projects so you can go and access it but don't worry about it we're going to |
| 21:56 | explain the whole structure during the project and you will be creating your |
| 22:00 | own repository and as well we have the link to the notion here we are doing the |
| 22:04 | project management here you're going to find the main steps the main phes of the |
| 22:08 | SQL projects that we will do and as well all the task that we will be doing |
| 22:12 | together during the projects and now we have links to the project tools so if |
| 22:17 | you don't have it already go and download the SQL Server Express so it's |
| 22:21 | like a server that going to run locally at your PC where your database going to |
| 22:24 | live another one that you have to download is the SQL Server management |
| 22:27 | Studio it is just a client in order to interact with the database and there |
| 22:32 | we're going to run all our queries and then link to the GitHub and as well link |
| 22:36 | to the draw AO if you don't have it already go and download it it is free |
| 22:40 | and amazing tool in order to draw diagrams so through the project we will |
| 22:44 | be drawing data models the data architecture a data lineage so a lot of |
| 22:49 | stuff we'll be doing using this tool so go and download it and the last thing it |
| 22:53 | is nice to have you have a link to the notion where you can go and create of |
| 22:57 | course free account accounts if you want to build the project plan and as well |
| 23:01 | Follow Me by creating the project steps and the project tasks okay so that's all |
| 23:06 | those are all the links for the projects so go and download all those stuff |
| 23:10 | create the accounts and once you are ready then we continue with the |
| 23:17 | projects all right so now I hope that you have downloaded all the tools and |
| 23:21 | created the accounts now it's time to move to very important step that's |
| 23:25 | almost all people skip while doing projects and then that is by creating |
| 23:30 | the project plan and for that we will be using the tool notion notion is of |
| 23:34 | course free tool and it can help you to organize your ideas your plans and |
| 23:39 | resources all in one place I use it very intensively for my private projects like |
| 23:44 | for example creating this course and I can tell you creating a project plan is |
| 23:47 | the key to success creating a data warehouse project is usually very |
| 23:51 | complex and according to Gardner reports over 50% of data warehouse projects fail |
| 23:57 | and my opinion about any complex project the key to success is to have a clear |
| 24:02 | project plan so now at this phase of the project we're going to go and create a |
| 24:06 | rough project plan because at the moment we don't have yet clear understanding |
| 24:11 | about the data architecture so let's go okay so now let's create a new page and |
| 24:15 | let's call it data warehouse projects the first thing is that we have to go |
| 24:18 | and create the main phases and stages of the projects and for that we need a |
| 24:23 | table so in order to do that hit slash and then type database in line and then |
| 24:28 | let's go and call it something like data warehouse epic and we're going to go and |
| 24:33 | hide it because I don't like it and then on the table we can go and rename it |
| 24:37 | like for example project epics something like that and now what we're going to do |
| 24:42 | we're going to go and list all the big task of the projects so an epic is |
| 24:45 | usually like a large task that needs a lot of efforts in order to solve it so |
| 24:49 | you can call it epics stages faces of the project whatever you want so we're |
| 24:53 | going to go and list our project steps so it start with the requirements |
| 24:58 | analyzes and then designing data architecture and another one we have the |
| 25:05 | project initialization so those are the three |
| 25:09 | big task in the project first and now what do we need we need another table |
| 25:13 | for the small chunks of the tasks the subtasks and we're going to do the same |
| 25:16 | thing so we're going to go and hit slash and we're going to search for the table |
| 25:20 | in line and we're going to do the same thing so first we're going to call it |
| 25:23 | data warehouse tasks and then we're going to hide it and over here we're |
| 25:27 | going to rename it and say this is the project tasks so now what we're going to |
| 25:32 | do we're going to go to the plus icon over here and then search for relation |
| 25:36 | this one over here with the arrow and now we're going to search for the name |
| 25:39 | of the first table so we called it data warehouse iix so let's go and click it |
| 25:45 | and we're going to say as well two-way relation so let's go and add the |
| 25:49 | relation so with that we got a fi in the new table called Data Warehouse iix this |
| 25:53 | comes from this table and as well we have here data warehouse tasks that |
| 25:57 | comes from from the below table so as you can see we have linked them together |
| 26:01 | now what I'm going to do I'm going to take this to the left side and then what |
| 26:04 | we're going to do we're going to go and select one of those epics like for |
| 26:07 | example let's take design the data architecture and now what we're going to |
| 26:11 | do we're going to go and break down this Epic into multiple tasks like for |
| 26:15 | example choose data management approach and then we have another task what we're |
| 26:20 | going to do we're going to go and select as well the same epic so maybe the next |
| 26:24 | step is brainstorm and design the layers and then let's go to another iic for |
| 26:31 | example the project initialization and we say over here for example create get |
| 26:36 | repo prepare the structure we can go and make another one in the same epic let's |
| 26:42 | say we're going to go and create the database and the schemas so as you can |
| 26:46 | see I'm just defining the subtasks of those epics so now what we're going to |
| 26:50 | do we're going to go and add a checkbox in order to understand whether we have |
| 26:53 | done the task or not so we go to the plus and search for check we need the |
| 26:57 | check box and what we're going to do we're going to make it really small like |
| 27:02 | this and with that each time we are done with the task we're going to go and |
| 27:05 | click on it just to make sure that we have done the task now there is one more |
| 27:09 | thing that is not really working nice and that is here we're going to have |
| 27:12 | like a long list of tasks and it's really annoying so what we're going to |
| 27:16 | do we're going to go to the plus over here and let's search for roll up so |
| 27:20 | let's go and select it so now what we're going to do we have to go and select the |
| 27:23 | relationship it's going to be that data warehouse task and after that we're |
| 27:26 | going to go to the property and make it as the check box so now as you can see |
| 27:29 | in the first table we are saying how many tasks is closed but I don't want to |
| 27:33 | show it like this what you going to do we're going to go to the calculation and |
| 27:36 | to the percent and then percent checked and with that we can see the progress of |
| 27:41 | our project and now instead of the numbers we can have really nice bar |
| 27:45 | great so as well we can go and give it a name like progress so that's it and we |
| 27:49 | can go and hide the data warehouse tasks and now with that we have really nice |
| 27:53 | progress bar for each epic and if we close all the tasks of this epic we can |
| 27:57 | see that we have reached 100% so this is the main structure now we can go and add |
| 28:01 | some cosmetics and rename stuff in order to make things looks nicer like for |
| 28:06 | example if I go to the tasks over here I can go and call it tasks and as well go |
| 28:11 | and change the icon to something like this and if you'd like to have an icon |
| 28:15 | for all those epics what we going to do we're going to go to the Epic for |
| 28:18 | example design data architecture and then if you hover on top of the title |
| 28:22 | you can see add an icon and you can go and pick any icon that you want so for |
| 28:27 | example this one and now now as you can see we have defined it here in the top |
| 28:30 | and the icon going to be as well in the pillow table okay so now one more thing |
| 28:34 | that we can do for the project tasks is that we can go and group them by the |
| 28:38 | epics so if you go to the three dots and then we go to groups and then we can |
| 28:42 | group up by the epics and as you can see now we have like a section for each epic |
| 28:47 | and you can go and sort the epics if you want if you go over here sort then |
| 28:51 | manual and you can go over here and start sorting the epics as you want and |
| 28:56 | with that you can expand and minimize each task if you don't want to see |
| 29:00 | always all tasks in one go so this is really nice way in order to build like |
| 29:04 | data management for your projects of course in companies we use professional |
| 29:08 | Tools in order to do projects like for example Gyra but for private person |
| 29:12 | projects that I do I always do it like this and I really recommend you to do it |
| 29:17 | not only for this project for any project that you are doing CU if you see |
| 29:20 | the whole project in one go you can see the big picture and closing tasks and |
| 29:24 | doing it like this these small things can makes you really satisfied and keeps |
| 29:28 | you motivated to finish the whole project and makes you proud okay friends |
| 29:33 | so now I just went and added few icons a rename stuff and as well more tasks for |
| 29:38 | each epic and this going to be our starting point in the project and once |
| 29:42 | we have more informations we're going to go and add more details on how exactly |
| 29:46 | we're going to build the data warehouse so at the start we're going to go and |
| 29:49 | analyze and understand the requirements and only after that we're going to start |
| 29:53 | designing the data architecture and here we have three tasks first we have to to |
| 29:58 | choose the data management approach and after that we're going to do |
| 30:01 | brainstorming and designing the layers of the data warehouse and at the end |
| 30:05 | we're going to go and draw a data architecture so with that we have clear |
| 30:10 | understanding how the data architecture looks like and after that we're going to |
| 30:13 | go to the next epic where we're going to start preparing our projects so once we |
| 30:17 | have clear understanding of the data architecture the first task here is to |
| 30:20 | go and create detailed project tasks so we're going to go and add more epes and |
| 30:25 | more tasks and once we are done then we're going to go and create the naming |
| 30:29 | conventions for the project just to make sure that we have rules and standards in |
| 30:33 | the whole project and next we're going to go and create a repository in the git |
| 30:37 | and we can to prepare as well the structure of the repository so that we |
| 30:40 | always commit our work there and then we can start with the first script where we |
| 30:44 | can create a database and schemas so my friends this is the initial plan for the |
| 30:49 | project now let's start with the first epic we have the requirements analyzes |
| 30:58 | now analyzing the requirement it is very important to understand which type of |
| 31:02 | data wehous you're going to go and build because there is like not only one |
| 31:05 | standard on how to build it and if you go blindly implementing the data |
| 31:09 | warehouse you might be doing a lot of stuff that is totally unnecessary and |
| 31:13 | you will be burning a lot of time so that's why you have to sit with the |
| 31:17 | stockholders with the department and understand what we exactly have to build |
| 31:21 | and depend on the requirements you design the shape of the data warehouse |
| 31:26 | so now let's go and analyze the requirement of this project now the |
| 31:28 | whole project is splitted into two main sections the first section we have to go |
| 31:33 | and build a data warehouse so this is a data engineering task and we will go and |
| 31:38 | develop etls and data warehouse and once we have done that we have to go and |
| 31:43 | build analytics and reporting business intelligence so we're going to do data |
| 31:47 | analysis but now first we will be focusing on the first part building the |
| 31:51 | data warehouse so what do you have here the statement is very simple it says |
| 31:56 | develop a modern data warehouse using SQL Server to consolidate sales data |
| 32:01 | enabling analytical reporting and informed decision making so this is the |
| 32:06 | main statements and then we have specifications the first one is about |
| 32:10 | the data sources it says import data from two Source systems Erb and CRM and |
| 32:15 | they are provided as CSV files and now the second task is talking about the |
| 32:20 | data quality we have to clean and fix data quality issues before we do the |
| 32:25 | data analyses because let's be real there is no R data that is perfect is |
| 32:29 | always missing and we have to clean that up now the next task is talking about |
| 32:33 | the integration so it says we have to go and combine both of the sources into one |
| 32:38 | single userfriendly data model that is designed for analytics and Reporting so |
| 32:44 | that means we have to go and merge those two sources into one single data model |
| 32:48 | and now we have here another specifications it says focus on the |
| 32:51 | latest data sets so there is no need for historization so that means we don't |
| 32:56 | have to go and build histories in the the database and the final requirement |
| 32:59 | is talking about the documentation so it says provide clear documentations of the |
| 33:03 | data model so that means the last product of the data warehouse to support |
| 33:08 | the business users and the analytical teams so that means we have to generate |
| 33:12 | a manual that's going to help the users that makes lives easier for the |
| 33:16 | consumers of our data so as you can see maybe this is very generic requirements |
| 33:20 | but it has a lot of information already for you so it's saying that we have to |
| 33:24 | use the platform SQL Server we have two Source systems using using the CSV files |
| 33:29 | and it sounds that we really have a bad data quality in the sources and as well |
| 33:33 | it wants us to focus on building completely new data model that is |
| 33:37 | designed for reporting and it says we don't have to do historization and it is |
| 33:42 | expected from us to generate documentations of the system so these |
| 33:46 | are the requirements for the data engineering part where we're going to go |
| 33:49 | and build a data warehouse that fulfill these requirements all right so with |
| 33:54 | that we have analyzed the requirements and as well we have closed at the first |
| 33:58 | easiest epic so we are done with this let's go and close it and now let's open |
| 34:02 | another one here we have to design the data architecture and the first task is |
| 34:07 | to choose data management approach so let's |
| 34:13 | go now designing the data architecture it is exactly like building a house so |
| 34:19 | before construction starts an architect going to go and design a plan a |
| 34:23 | blueprint for the house how the rooms will be connected how to make the house |
| 34:27 | functional safe and wonderful and without this blueprint from The |
| 34:31 | Architects the builders might create something unstable inefficient or maybe |
| 34:35 | unlivable the same goes for data projects a data architect is like a |
| 34:39 | house architect they design how your data will flow integrate and be accessed |
| 34:44 | so as data Architects we make sure that the data warehouse is not only |
| 34:48 | functioning but also scalable and easy to maintain and this is exactly what we |
| 34:52 | will do now we will play the role of the data architect and we will start |
| 34:56 | brainstorming and designing the architecture of the data warehouse so |
| 35:00 | now I'm going to show you a sketch in order to understand what are the |
| 35:03 | different approaches in order to design a data architecture and this phase of |
| 35:07 | the projects usually is very exciting for me because this is my main role in |
| 35:11 | data projects I am a data architect and I discuss a lot of different projects |
| 35:16 | where we try to find out the best design for the projects all right so now let's |
| 35:23 | go now the first step of building a data architecture is to make very important |
| 35:28 | decision to choose between four major types the first approach is to build a |
| 35:33 | data warehouse it is very suitable if you have only structured data and your |
| 35:37 | business want to build solid foundations for reporting and business intelligence |
| 35:42 | and another approach is to build a data leak this one is way more flexible than |
| 35:47 | a data warehouse where you can store not only structured data but as well semi |
| 35:51 | and unstructured data we usually use this approach if you have mixed types of |
| 35:56 | data like database tables locks images videos and your business want to focus |
| 36:00 | not only on reporting but as well on Advanced analytics or machine learning |
| 36:05 | but it's not that organized like a data warehouse and data leaks if it's too |
| 36:09 | much unorganized can turns into Data swamp and this is where we need the next |
| 36:14 | approach so the next one we can go and build data leak house so it is like a |
| 36:18 | mix between data warehouse and data leak you get the flexibility of having |
| 36:23 | different types of data from the data Lake but you still want to structure and |
| 36:27 | organiz your data like we do in the data warehouse so you mix those two words |
| 36:31 | into one and this is a very modern way on how to build data Architects and this |
| 36:35 | is currently my favorite way of building data management system now the last and |
| 36:39 | very recent approach is to build data Mish so this is a little bit different |
| 36:43 | instead of having centralized data management system the idea now in the |
| 36:47 | data Mish is to make it decentralized you cannot have like one centralized |
| 36:51 | data management system because always if you say centralized then it means |
| 36:55 | bottleneck so instead you have multiple departments and multiple domains where |
| 36:59 | each one of them is building a data product and sharing it with others so |
| 37:03 | now you have to go and pick one of those approaches and in this project we will |
| 37:07 | be focusing on the data warehouse so now the question is how to build the data |
| 37:11 | warehouse well there is as well four different approaches on how to build it |
| 37:15 | the first one is the inone approach so again you have your sources and the |
| 37:19 | first layer you start with the staging where the row data is landing and then |
| 37:23 | the next layer you organize your data in something called Enterprise data |
| 37:27 | Warehouse where you go and model the data using the third normal format it's |
| 37:32 | about like how to structure and normalize your tables so you are |
| 37:36 | building a new integrated data model from the multiple sources and then we go |
| 37:40 | to the third layer it's called the data Mars where you go and take like small |
| 37:44 | subset of the data warehouse and you design it in a way that is ready to be |
| 37:49 | consumed from reporting and it focus on only one toque like for example the |
| 37:53 | customers sales or products and after that you go and connect your bi tool |
| 37:58 | like powerbi or Tableau to the data Mars so with that you have three layers to |
| 38:02 | prepare the data before reporting now moving on to the next one we have the |
| 38:06 | kle approach he says you know what building this Enterprise data warehouse |
| 38:10 | it is wasting a lot of time so what we can do we can jump immediately from the |
| 38:15 | stage layer to the final data marks because building this Enterprise data |
| 38:19 | warehouse it is a big struggle and usually waste a lot of time so he always |
| 38:23 | want you to focus and building the data marks quickly as possible so it is |
| 38:28 | faster approach than Inon but with the time you might get chaos in the data |
| 38:32 | Mars because you are not always focusing in the big picture and you might be |
| 38:35 | repeating same Transformations and Integrations in different data Mars so |
| 38:40 | there is like trade-off between the speed and consistent data warehouse now |
| 38:44 | moving on to the third approach we have the Data Vault so we still have the |
| 38:48 | stage and the data Mars but it says we still need this Central Data Warehouse |
| 38:53 | in the middle but this middle layer we're going to bring more standards and |
| 38:56 | rules so it tells you to split this middle layer into two layers the row |
| 39:01 | Vault and the business vault in the row Vault you have the original data but in |
| 39:06 | the business Vault you have all the business rules and Transformations that |
| 39:09 | prepares the data for the data Mars so Data Vault it is very similar to the in |
| 39:13 | one but it brings more standards and rules to the middle layer now I'm going |
| 39:18 | to go and add a fourth one that I'm going to call it Medallion architecture |
| 39:23 | and this one is my favorite one because it is very easy to understand and to |
| 39:27 | build so it says you're going to go and build three layers bronze silver and |
| 39:31 | gold the bronze layer it is very similar to the stage but we have understood with |
| 39:35 | the time that the stage layer is very important because having the original |
| 39:39 | data as it is it going to helps a lot by tracebility and finding issues then the |
| 39:44 | next layer we have the silver layer it is where we do Transformations data |
| 39:48 | cleansy but we don't apply yet any business rules now moving on to the last |
| 39:52 | layer the gold layer it is as well very similar to the data Mars but there we |
| 39:56 | can build different typ type of objects not only for reporting but as well for |
| 40:00 | machine learning for AI and for many different purposes so they are like |
| 40:05 | business ready objects that you want to share as a data product so those are the |
| 40:10 | four approaches that you can use in order to build a data warehouse so again |
| 40:14 | if you are building a data architecture you have to specify which approach you |
| 40:18 | want to follow so at the start we said we want to build a data warehouse and |
| 40:22 | then we have to decide between those four approaches on how to build the data |
| 40:25 | warehouse and in this project we will be using using The Medallion architecture |
| 40:29 | so this is a very important question that you have to answer as the first |
| 40:32 | step of building a data architecture all right so with that we have decided on |
| 40:36 | the approach so we can go and Mark it as done the next step we're going to go and |
| 40:40 | design the layers of the data |
| 40:46 | warehouse now there is like not 100% standard way and rules for each layer |
| 40:52 | what you have to do as a data architect you have to Define exactly what is the |
| 40:57 | purpose of each layer so we start with the bronze layer so we say it going to |
| 41:01 | store row and unprocessed data as it is from the sources and why we are doing |
| 41:06 | that it is for tracebility and debugging if you have a layer where you are |
| 41:10 | keeping the row data it is very important to have the data as it is from |
| 41:13 | the sources because we can go always back to the pron layer and investigate |
| 41:18 | the data of specific Source if something goes wrong so the main objective is to |
| 41:22 | have row untouched data that's going to helps you as a data engineer by |
| 41:27 | analyzing the road cause of issues now moving on to the silver layer it is the |
| 41:31 | layer where we're going to store clean and standardized data and this is the |
| 41:35 | place where we're going to do basic transformations in order to prepare the |
| 41:39 | data for the final layer now for the good layer it going to contain business |
| 41:43 | ready data so the main goal here is to provide data that could be consumed by |
| 41:48 | business users and analysts in order to build reporting and analytics so with |
| 41:52 | that we have defined the main goal for each layer now next what I would like to |
| 41:56 | do is to to define the object types and since we are talking about a data |
| 42:00 | warehouse in database we have here generally two types either a table or a |
| 42:04 | view so we are going for the bronze layer and the silver layer with tables |
| 42:08 | but for the gold layer we are going with the views so the best practice says for |
| 42:12 | the last layer in your data warehouse make it virtual using views it going to |
| 42:17 | gives you a lot of dynamic and of course speed in order to build it since we |
| 42:20 | don't have to make a load process for it and now the next step is that we're |
| 42:24 | going to go and Define the load method so in this project I have decided to go |
| 42:27 | with the full load using the method of trating and inserting it is just faster |
| 42:32 | and way easier so we're going to say for the pron layer we're going to go with |
| 42:34 | the full load and you have to specify as well for the silver layer as well we're |
| 42:38 | going to go with the full load and of course for the views we don't need any |
| 42:41 | load process so each time you decide to go with tables you have to define the |
| 42:45 | load methods with full load incremental loads and so on now we come to the very |
| 42:49 | interesting part the data Transformations now for the pron layer |
| 42:53 | it is the easiest one about this topic because we don't have any |
| 42:56 | transformations we have to commit ourself to not touch the data do not |
| 43:01 | manipulate it don't change anything so it's going to stay as it is if it comes |
| 43:05 | bad it's going to stay bad in the bronze layer and now we come to the silver |
| 43:08 | layer where we have the heavy lifting as we committed in the objective we have to |
| 43:12 | make clean and standardized data and for that we have different types of |
| 43:16 | Transformations so we have to do data cleansing data standardizations data |
| 43:20 | normalizations we have to go and derive new columns and data enrichment so there |
| 43:25 | are like bunch of trans transformation that we have to do in order to prepare |
| 43:29 | the data our Focus here is to transform the data to make it clean and following |
| 43:34 | standards and try to push all business transformations to the next layer so |
| 43:38 | that means in the god layer we will be focusing on business Transformations |
| 43:43 | that is needed for the consumers for the use cases so what we do here we do data |
| 43:47 | Integrations between Source system we do data aggregations we apply a lot of |
| 43:51 | business Logics and rules and we build a data model that is ready for for example |
| 43:56 | business inions so here we do a lot of business Transformations and in the |
| 44:00 | silver layer we do basic data Transformations so it is really here |
| 44:04 | very important to make the fine decisions what type of transformations |
| 44:09 | to be done in each layer and make sure that you commit to those rules now the |
| 44:13 | next aspect is about the data modeling in the bronze layer and the silver layer |
| 44:17 | we will not break the data model that comes from the source system so if the |
| 44:21 | source system deliver five tables we're going to have here like five tables and |
| 44:24 | as well in the silver layer we will not go and D normalize or normalize or like |
| 44:29 | make something new we're going to leave it exactly like it comes from the source |
| 44:32 | system because what we're going to do we're going to build the data model in |
| 44:36 | the gold layer and here you have to Define which data model you want to |
| 44:39 | follow are you following the star schema the snowflake or are you just making |
| 44:43 | aggregated objects so you have to go and make a list of all data models types |
| 44:47 | that you're going to follow in the gold layer and at the end what you can |
| 44:50 | specify in each layer is the target audience and this is of course very |
| 44:54 | important decision in the bronze layer you don't want to give access access to |
| 44:57 | any end user it is really important to make sure that only data Engineers |
| 45:01 | access the bronze layer it makes no sense for data analysts or data |
| 45:05 | scientist to go to the bad data because you have a better version for that in |
| 45:10 | the silver layer so in the silver layer of course the data Engineers have to |
| 45:13 | have an access to it and as well the data analysts and the data scientist and |
| 45:17 | so on but still you don't give it to any business user that can't deal with the |
| 45:22 | row data model from the sources because for the business users you're going to |
| 45:26 | get a bit layer for them and that is the gold layer so the gold layer it is |
| 45:30 | suitable for the data analyst and as well the business users because usually |
| 45:35 | the business users don't have a deep knowledge on the technicality of the |
| 45:38 | Sero layer so if you are designing multiple layers you have to discuss all |
| 45:42 | those topics and make clear decision for each layer all right my friends so now |
| 45:47 | before we proceed with the design I want to tell you a secret principle Concepts |
| 45:51 | that each data architect must know and that is the separation of concerns so |
| 45:57 | what is that as you are designing an architecture you have to make sure to |
| 46:00 | break down the complex system into smaller independent parts and each part |
| 46:05 | is responsible for a specific task and here comes the magic the component of |
| 46:10 | your architecture must not be duplicated so you cannot have two parts are doing |
| 46:15 | the same thing so the idea here is to not mix everything and this is one of |
| 46:20 | the biggest mistakes in any big projects and I have sewn that almost everywhere |
| 46:25 | so a good data architect follow this concept this principle so for example if |
| 46:30 | you are looking to our data architecture we have already done that so we have |
| 46:34 | defined unique set of tasks for each layer so for example we have said in the |
| 46:38 | silver layer we do data cleansing but in the gold layer we do business |
| 46:43 | Transformations and with that you will not be allowing to do any business |
| 46:47 | transformations in the silver layer and the same thing goes for the gold layer |
| 46:50 | you don't do in the gold layer any data cleansing so each layer has its own |
| 46:54 | unique tasks and the same thing goes for the pron layer and the silver layer you |
| 46:59 | do not allow to load data from The Source systems directly to the silver |
| 47:03 | layer because we have decided the landing layer the first layer is the |
| 47:07 | pron layer otherwise you will have like set of source systems that are loaded |
| 47:11 | first to the pron layer and another set is skipping the layer and going to the |
| 47:16 | silver and with that we have overlapping you are doing data inje in two different |
| 47:20 | layers so my friends if you have this mindsets separation of concerns I |
| 47:25 | promise you you're going to be a data architect so think about it all right my |
| 47:29 | friends so with that we have designed the layers of the data warehouse we can |
| 47:33 | go and close it the next step we're going to go to draw o and start drawing |
| 47:37 | the data |
| 47:41 | architecture so there is like no one standard on how to build a data |
| 47:45 | architecture you can add your style and the way that you want so now the first |
| 47:49 | thing that we have to show in data architecture is the different layers |
| 47:52 | that we have the first layer is the source system layer so let's go and take |
| 47:56 | a box like this and make it a little bit bigger and I'm just going to go and make |
| 48:00 | the design so I'm going to remove the fill and make the line dotted one and |
| 48:04 | after dots I'm going to go and change maybe the color to something like this |
| 48:07 | gray so now we have like a container for the first layer and then we have to go |
| 48:11 | and add like a text on top of it so what I'm going to do I'm going to take |
| 48:15 | another box let's go and type inside it sources and I'm going to go and style it |
| 48:19 | so I'm going to go to the text and make it maybe 24 and then remove the lines |
| 48:24 | like this make it a little bit smaller and put it on top so this is the first |
| 48:29 | layer this is where the data come from and then the data going to go inside a |
| 48:33 | data warehouse so I'm just going to go and duplicate this one this one is the |
| 48:37 | data |
| 48:41 | warehouse all right so now the third layer what is going to be it's going to |
| 48:45 | be the consumers who will be consuming this data warehouse so I'm going to put |
| 48:50 | another box and say this is the consume layer okay so those are the three |
| 48:55 | containers now inside the data warehouse we have decided to build it using the |
| 48:59 | Medan architecture so we're going to have three layers inside the warehouse |
| 49:03 | so I'm going to take again another box I'm going to call this one this is the |
| 49:08 | bronze layer and now we have to go and put a design for it so I'm going to go |
| 49:12 | with this color over here and then the text and maybe something like 20 and |
| 49:17 | then make it a little bit smaller and just put it here and beneath that we're |
| 49:22 | going to have the component so this is just a title of a container so I'm going |
| 49:26 | to have it like this this remove the text from inside it and remove the |
| 49:30 | filling so this container is for the bronze layer let's go and duplicate it |
| 49:35 | for the next one so this one going to be the silver |
| 49:39 | layer and of course we can go and change the coloring to gray because it is |
| 49:43 | silver and as well the lines and remove the filling great and now maybe I'm |
| 49:48 | going to make the font as bold all right now the third layer going to be the gold |
| 49:54 | layer and we have to go and pick it color for that so style and here we have |
| 49:59 | like something like yellow the same thing for the container I remove the |
| 50:03 | filling so with that we are showing now the different layers inside our data |
| 50:07 | warehouse now those containers are empty what we're going to do we're going to go |
| 50:10 | inside each one of them and start adding contents so now in the sources it is |
| 50:14 | very important to make it clear what are the different types of source system |
| 50:18 | that you are connecting to the data warehouse because in real project there |
| 50:21 | are like multiple types you might have a database API files CFA and here it's |
| 50:26 | important to show those different types in our projects we have folders and |
| 50:29 | inside those folders We have CSV files so now what you have to do we have to |
| 50:33 | make it clear in this layer that the input for our project is CSV file so it |
| 50:38 | really depend how you want to show that I'm going to go over here and say maybe |
| 50:42 | folder and then I'm going to go and take the folder and put it here inside and |
| 50:45 | then maybe search for file more results and go pick one of those icons for |
| 50:50 | example I'm going to go with this one over here so I'm going to make it |
| 50:53 | smaller and add it on top of the folder so with that we make it clear for |
| 50:57 | everyone seeing the architecture that the sources is not a database is not an |
| 51:02 | API it is a file inside the folder so now very important here to show is the |
| 51:07 | source systems what are the sources that is involved in the project so here what |
| 51:10 | we're going to do we're going to go and give it a name for example we have one |
| 51:13 | source called CRM B like this and maybe make the icon and we have another source |
| 51:18 | called Erp so we going to go and duplicate it put it over here and then |
| 51:22 | rename it Erp so now it is for everyone clear we have two sources for the this |
| 51:26 | project and the technology is used is simply a file so now what we can do as |
| 51:30 | well we can go and add some descriptions inside this box to make it more clear so |
| 51:34 | what I'm going to do I'm going to take a line because I want to split the |
| 51:37 | description from the icons something like this and make it gray and then |
| 51:41 | below it we're going to go and add some text and we're going to say is CSV file |
| 51:47 | and the next point and we can say the interface is simply files in folder and |
| 51:53 | of course you can go and add any specifications and explanation about the |
| 51:57 | sources if it is a database you can see the type of the database and so on so |
| 52:01 | with that we made it in the data architecture clear what are the sources |
| 52:04 | of our data warehouse and now the next step what we're going to do we're going |
| 52:07 | to go and design the content of the bronze silver and gold so I'm going to |
| 52:11 | start by adding like an icon in each container it is to show about that we |
| 52:15 | are talking about database so what we're going to do we're going to go and search |
| 52:18 | for database and then more result more results I'm going to go with this icon |
| 52:24 | over here so let's go and make it it's bigger something like this maybe change |
| 52:29 | the color of that so we're going to have the bronze and as well here the silver |
| 52:34 | and the gold so now what we're going to do we're going to go and add some arrows |
| 52:37 | between those layers so we're going to go over here so we can go and search for |
| 52:41 | Arrow and maybe go and pick one of those let's go and put it here and we can go |
| 52:45 | and pick a color for that maybe something like this and adjust it so now |
| 52:50 | we can have this nice Arrow between all the layers just to explain the direction |
| 52:54 | of our architecture right so we can read this from left to right and as well |
| 52:58 | between the gold layer and the consume okay so now what I'm going to do next |
| 53:02 | we're going to go and add one statement about each layer the main objective so |
| 53:07 | let's go and grab a text and put it beneath the database and we're going to |
| 53:11 | say for example for the bl's layer it's going to be the row data maybe make the |
| 53:15 | text bigger so you are the row data and then the next one in the silver you are |
| 53:21 | cleans standard data and then the last one for the gos we can say |
| 53:27 | business ready data so with that we make the |
| 53:31 | objective clear for each layer now below all those icons what we going to do |
| 53:34 | we're going to have a separator again like this make it like colored and |
| 53:39 | beneath it we're going to add the most important specifications of this layer |
| 53:43 | so let's go and add those separators in each layer okay so now we need a text |
| 53:48 | below it let's take this one here so what is the object type of the bronze |
| 53:53 | layer it's going to be a table and we can go and add the load methods we say |
| 53:58 | this is patch processing since we are not doing streaming we can say it is a |
| 54:03 | full load we are not doing incremental load so we can say here |
| 54:08 | Tran and insert and then we add one more section maybe about the Transformations |
| 54:14 | so we can say no Transformations and one more about the |
| 54:18 | data model we're going to say none as is and now what I'm going to do I'm going |
| 54:23 | to go and add those specifications as well for the silver and gold so here |
| 54:26 | what we have discussed the object type the load process the |
| 54:29 | Transformations and whether we are breaking the data model or not the same |
| 54:34 | thing for the gold layer so I can say with that we have really nice layering |
| 54:38 | of the data warehouse and what we are left is with the consumers over here you |
| 54:42 | can go and add the different use cases and tools that can access your data |
| 54:45 | warehouse like for example I'm adding here business intelligence and Reporting |
| 54:49 | maybe using poweri or Tau or you can say you can access my data warehouse in |
| 54:53 | order to do atoc analyzes using the SQ queries and this is what we're going to |
| 54:58 | focus on the projects after we buil the data warehouse and as well you can offer |
| 55:02 | it for machine learning purposes and of course it is really nice to add some |
| 55:05 | icons in your architecture and usually I use this nice websites called Flat icon |
| 55:10 | it has really amazing icons that you can go and use it in your architecture now |
| 55:14 | of course we can go and keep adding icons and stuff to explain the data |
| 55:17 | architecture and as well the system like for example it is very important here to |
| 55:21 | say which tools you are using in order to build this data warehouse is it in |
| 55:25 | the cloud are you using Azure data breaks or maybe snowflake so we're going |
| 55:29 | to go and add for our project the icon of SQL Server since we are building this |
| 55:34 | data warehouse completely in the SQL Server so for now I'm really happy about |
| 55:38 | it as you can see we have now a plan right all right guys so with that we |
| 55:41 | have designed the data architecture using the drw O and with that we have |
| 55:45 | done the last step in this epic and now with that we have a design for the data |
| 55:49 | architecture and we can say we have closed this epic now let's go to the |
| 55:53 | next one we will start doing the first step to prepare our projects and the |
| 55:57 | first task here is to create a detailed project |
| 56:03 | plan all right my friends so now it's clear for us that we have three layers |
| 56:07 | and we have to go and build them so that means our big epic is going to be after |
| 56:11 | the layers so here I have added three more epics so we have build bronze layer |
| 56:16 | build silver layer and gold layer and after that I went and start defining all |
| 56:22 | the different tasks that we have to follow in the projects so at the start |
| 56:26 | will be analyzing then coding and after that we're going to go and do testing |
| 56:30 | and once everything is ready we're going to go and document stuff and at the end |
| 56:34 | we have to commit our work in the get repo all those epics are following the |
| 56:39 | same like pattern in the tasks so as you can see now we have a very detailed |
| 56:43 | project structure and now things are more cleared for us how we going to |
| 56:47 | build the data warehouse so with that we are done from this task and now the next |
| 56:52 | task we have to go and Define the naming Convention of the projects |
| 57:00 | all right so now at this phase of the projects we usually Define the naming |
| 57:03 | conventions so what is that it a set of rules that you define for naming |
| 57:09 | everything in the projects whether it is a database schema tables start |
| 57:13 | procedures folders anything and if you don't do that at the early phase of the |
| 57:18 | project I promise you chaos can happen because what going to happen you will |
| 57:22 | have different developers in your projects and each of those developers |
| 57:25 | have their own style of course so one developer might name a tabled Dimension |
| 57:30 | customers where everything is lowercase and between them underscore and you have |
| 57:34 | another developer creating another table called Dimension products but using the |
| 57:39 | camel case so there is no separation between the words and the first |
| 57:42 | character is capitalized and maybe another one using some prefixes like di |
| 57:46 | imore categories so we have here like a shortcut of the dimension so as you can |
| 57:51 | see there are different designs and styles and if you leave the door open |
| 57:55 | what can happen in the middle of the projects you will notice okay everything |
| 57:58 | looks inconsistence and you can define a big task to go and rename everything |
| 58:04 | following specific role so instead of wasting all this time at this phase you |
| 58:09 | go and Define the naming conventions and let's go and do that so we will start |
| 58:13 | with a very important decision and that is which naming convention we going to |
| 58:17 | follow in the whole project so you have different cases like the camel case the |
| 58:22 | Pascal case the Kebab case and the snake case and for this project we're going to |
| 58:27 | go with the snake case where all the letters of award going to be lowercase |
| 58:33 | and the separation between wordss going to be an underscore for example a table |
| 58:37 | name called customer info customer is lowercased info is as well lowercased |
| 58:42 | and between them an underscore so this is always the first thing that you have |
| 58:46 | to decide for your data project the second thing is to decide the language |
| 58:51 | so for example I work in Germany and there is always like a decision that we |
| 58:54 | have to make whether we use Germany or English so we have to decide for our |
| 58:58 | project which language we're going to use and a very important general rule is |
| 59:03 | that avoid reserved words so don't use a square reserved word as an object name |
| 59:08 | like for example table don't give a table name as a table so those are the |
| 59:13 | general principles so those are the general rules that you have to follow in |
| 59:17 | the whole project this applies for everything for tables columns start |
| 59:21 | procedures any names that you are giving in your scripts now moving on we have |
| 59:26 | specifications for the table names and here we have different set of rules for |
| 59:30 | each layer so here the rule says Source system uncore entity so we are saying |
| 59:35 | all the tables in the bronze layer should start first with the source |
| 59:39 | system name like for example CRM or Erb and after that we have an underscore and |
| 59:44 | then at the end we have the entity name or the table name so for example we have |
| 59:49 | this table name CRM uncore so that means this table comes from the source system |
| 59:54 | CRM and then we have the table name the entity name customer info so this is the |
| 59:59 | rule that we're going to follow in naming all tables in the pron layer then |
| 1:00:03 | moving on to the silver layer it is exactly like the bronze because we are |
| 1:00:07 | not going to rename anything we are not going to build any new data model so the |
| 1:00:12 | naming going to be one to one like the bronze so it is exactly the same rules |
| 1:00:17 | as the bronze but if we go to the gold here since we are building new data |
| 1:00:21 | model we have to go and rename things and since as well we are integrating |
| 1:00:25 | multi sources together we will not be using the source system name in the |
| 1:00:30 | tables because inside one table you could have multiple sources so the rule |
| 1:00:34 | says all the names must be meaningful business aligned names for the tables |
| 1:00:39 | starting with the category prefix so here the rule says it start with |
| 1:00:43 | category then underscore and then entity now what is category we have in the go |
| 1:00:48 | layer different types of tables so we could build a table called a fact table |
| 1:00:53 | another one could be a dimension a third type could be an aggregation or report |
| 1:00:58 | so we have different types of tables and we can specify those types as a perect |
| 1:01:03 | at the start so for example we are seeing here effect uncore sales so the |
| 1:01:09 | category is effect and the table name called sales and here I just made like a |
| 1:01:13 | table with different type of patterns so we could have a dimension so we say it |
| 1:01:18 | start with the di imore for example the IM customers or products and then we |
| 1:01:23 | have another type called fact table so it starts with fact underscore or |
| 1:01:27 | aggregated table where we have the fair three characters like aggregating the |
| 1:01:31 | customers or the sales monthly so as you can see as you are creating a naming |
| 1:01:35 | convention you have first to make it clear what is the rule describe each |
| 1:01:40 | part of the rule and start giving examples so with that we make it clear |
| 1:01:44 | for the whole team which names they should follow so we talked here about |
| 1:01:48 | the table naming convention then you can as well go and make naming convention |
| 1:01:52 | for the columns like for example in the gold layer we're going to go and have |
| 1:01:56 | circuit keys so we can Define it like this the circuit key should start with a |
| 1:02:00 | table name and then underscore a key like for example we can call it customer |
| 1:02:04 | underscore key it is a surrogate key in the dimension customers the same thing |
| 1:02:09 | for technical columns as a data engineer we might add our own columns to the |
| 1:02:13 | tables that don't come from the source system and those columns are the |
| 1:02:17 | technical columns or sometimes we call them metadata columns now in order to |
| 1:02:21 | separate them from the original columns that comes from the source system |
| 1:02:26 | we can have like a prefix for that like for example the rule says if you are |
| 1:02:30 | building any technical or metadata columns the column should start with |
| 1:02:35 | dwore and then that column name for example if you want the metadata load |
| 1:02:39 | date we can have dwore load dates so with that if anyone |
| 1:02:44 | sees that column starts with DW we understand this data comes from a data |
| 1:02:49 | engineer and we can keep adding rules like for example the St procedure over |
| 1:02:53 | here if you are making an ETL script then it should should start with the |
| 1:02:56 | prefix load uncore and then the layer for example the St procedure that is |
| 1:03:01 | responsible for loading the bronze going to be called load uncore bronze and for |
| 1:03:06 | the Silver Load uncore silver so those are currently the rules for the St |
| 1:03:11 | procedure so this is how I do it usually in my projects all right my friends so |
| 1:03:14 | with do we have a solid namey conventions for our projects so this is |
| 1:03:18 | done and now the next with that we're going to go to git and you will create a |
| 1:03:21 | brand new repository and we're going to prepare its structure so let's go |
| 1:03:29 | go all right so now we come to as well important step in any projects and |
| 1:03:33 | that's by creating the git repository so if you are new to git don't worry about |
| 1:03:37 | it it is simpler than it sounds so it's all about to have a safe place where you |
| 1:03:41 | can put your codes that you are developing and you will have the |
| 1:03:44 | possibility to track everything happen to the codes and as well you can use it |
| 1:03:48 | in order to collaborate with your team and if something goes wrong you can |
| 1:03:52 | always roll back and the best part here once you are done with the project you |
| 1:03:55 | can share your reposter as a part of your portfolio and it is really amazing |
| 1:03:59 | thing if you are applying for a job by showcasing your skills that you have |
| 1:04:03 | built a data warehouse by using well documented get reposter so now let's go |
| 1:04:07 | and create the reposter of the project now we are at the overview of our |
| 1:04:11 | account so the first thing that you have to do is to go to the repos stories over |
| 1:04:15 | here and then we're going to go to this green button and click on you the first |
| 1:04:19 | thing that we have to do is to give Theory name so let's call it SQL data |
| 1:04:24 | warehouse project and then here we can go and give it a description so for |
| 1:04:29 | example I'm saying building a modern data warehouse with SQL Server now the |
| 1:04:33 | next option whether you want to make it public and private I'm going to leave it |
| 1:04:37 | as a public and then let's go and add here a read me file and then here about |
| 1:04:42 | the license we can go over here and select the MIT MIT license gives |
| 1:04:46 | everyone the freedom of using and modifying your code okay so I think I'm |
| 1:04:51 | happy with the setup let's go and create the repost story and with that we have |
| 1:04:55 | our brand new reposter now the next step that I usually do is to create the |
| 1:05:00 | structure of the reposter and usually I always follow the same patterns in any |
| 1:05:04 | projects so here we need few folders in order to put our files right so what I |
| 1:05:09 | usually do I go over here to add file create a new file and I start creating |
| 1:05:14 | the structure over here so the first thing is that we need data sets then |
| 1:05:18 | slash and with that the repos you can understand this is a folder not a file |
| 1:05:22 | and then you can go and add anything like here play holder just an empty file |
| 1:05:28 | this just can to help me to create the folders so let's go and commit so commit |
| 1:05:32 | the changes and now if you go back to the main projects you can see now we |
| 1:05:36 | have a folder called data sets so I'm going to go and keep creating stuff so I |
| 1:05:41 | will go and create the documents placeholder commit the changes and then |
| 1:05:46 | I'm going to go and create the scripts Place |
| 1:05:51 | holder and the final one what I usually add is the the |
| 1:05:56 | tests something like this so with that as you can see now we have the main |
| 1:06:01 | folders of our repository now what I usually do the next with that I'm going |
| 1:06:05 | to go and edit the main readme so you can see it over here as well so what |
| 1:06:09 | we're going to do we're going to go inside the read me and then we're going |
| 1:06:12 | to go to the edit button here and we're going to start writing the main |
| 1:06:16 | information about our project this is really depend on your style so you can |
| 1:06:19 | go and add whatever you want this is the main page of your repository and now as |
| 1:06:25 | you can see the file name here ismd it stands for markdown it is just an easy |
| 1:06:31 | and friendly format in order to write a text so if you have like documentations |
| 1:06:35 | you are writing a text it is a really nice format in order to organize it |
| 1:06:39 | structure it and it is very friendly so what I'm going to do at the start I'm |
| 1:06:43 | going to give a few description about the project so we have the main title |
| 1:06:47 | and then we have like a welcome message and what this reposter is about and in |
| 1:06:51 | the next section maybe we can start with the project requirements and then maybe |
| 1:06:55 | at the end you can say few words about the licensing and few words about you so |
| 1:07:01 | as you can see it's like the homepage of the project and the repository so once |
| 1:07:04 | you are done we're going to go and commit the changes and now if you go to |
| 1:07:08 | the main page of the repository you can see always the folder and files at the |
| 1:07:13 | start and then below it we're going to see the informations from the read me so |
| 1:07:17 | again here we have the welcome statement and then the projects requirements and |
| 1:07:22 | at the end we have the licensing and about me so my friends that's that's it |
| 1:07:25 | we have now a repost story and we have now the main structure of the projects |
| 1:07:30 | and through the projects as we are building the data warehouse we're going |
| 1:07:33 | to go and commit all our work in this repository nice right all right so with |
| 1:07:38 | that we have now your repository ready and as we go in the projects we will be |
| 1:07:43 | adding stuff to it so this step is done and now the last step finally we're |
| 1:07:47 | going to go to the SQL server and we're going to write our first scripts where |
| 1:07:51 | we're going to create a database and schemas |
| 1:07:58 | all right now the first step is we have to go and create brand new database so |
| 1:08:02 | now in order to do that first we have to switch to the database master so you can |
| 1:08:06 | do it like this use master and semicolon and if you go and execute it now we are |
| 1:08:11 | switched to the master database it is a system database in SQL Server where you |
| 1:08:15 | can go and create other databases and you can see from the toolbar that we are |
| 1:08:19 | now logged into the master database now the next step we have to go and create |
| 1:08:24 | our new database so we're going to say say create database and you can call it |
| 1:08:28 | whatever you want so I'm going to go with data warehouse semicolon let's go |
| 1:08:33 | and execute it and with that we have created our database let's go and check |
| 1:08:37 | it from the object Explorer let's go and refresh and you can see our new data |
| 1:08:41 | warehouse this is our new database awesome right now to the next step we're |
| 1:08:45 | going to go and switch to the new database so we're going to say use data |
| 1:08:50 | warehouse and semicolon so let's go and switch to it and you can see now now we |
| 1:08:55 | are logged into the data warehouse database and now we can go and start |
| 1:08:59 | building stuff inside this data warehouse so now the first step that I |
| 1:09:03 | usually do is I go and start creating the schemas so what is the schema think |
| 1:09:07 | about it it's like a folder or a container that helps you to keep things |
| 1:09:12 | organized so now as we decided in the architecture we have three layers bronze |
| 1:09:16 | silver gold and now we're going to go and create for each layer a schema so |
| 1:09:20 | let's go and do that we're going to start with the first one create schema |
| 1:09:24 | and the first one is bronze so let's do it like this and a semicolon let's go |
| 1:09:29 | and create the first schema nice so we have new schema let's go to our database |
| 1:09:34 | and then in order to check the schemas we go to the security and then to the |
| 1:09:38 | schemas over here and as you can see we have the bronze and if you don't find it |
| 1:09:42 | you have to go and refresh the whole schemas and then you will find the new |
| 1:09:46 | schema great so now we have the first schema now what we're going to do we're |
| 1:09:49 | going to go and create the others two so I'm just going to go and duplicate it so |
| 1:09:53 | the next one going to be the silver and the third one going to be the golds so |
| 1:09:57 | let's go and execute those two together we will get an error and that's because |
| 1:10:02 | we are not having the go in between so after each command let's have a go and |
| 1:10:07 | now if I highlight the silver and gold and then execute it will be working the |
| 1:10:12 | go in SQL it is like separator so it tells SQL first execute completely the |
| 1:10:18 | First Command before go to the next one so it is just separator now let's go to |
| 1:10:22 | our schemas refresh and now we can see as well we have the gold and the silver |
| 1:10:27 | so with this we have now a database we have the three layers and we can start |
| 1:10:31 | developing each layer |
| 1:10:37 | individually okay so now let's go and commit our work in the git so now since |
| 1:10:41 | it is a script and code we're going to go to the folder scripts over here and |
| 1:10:45 | then we're going to go and add a new file let's call it init database.sql and |
| 1:10:50 | now we're going to go and paste our code over here so now I have done few |
| 1:10:54 | modifications like for example before we create the database we have to check |
| 1:10:59 | whether the database exists this is an important step if you are recreating the |
| 1:11:03 | database otherwise if you don't do that you will get an error where it's going |
| 1:11:06 | going to say the database already exists so first it is checking whether the |
| 1:11:11 | database exist then it drops it I have added few comments like here we are |
| 1:11:15 | saying creating the data warehouse creating the schemas and now we have a |
| 1:11:19 | very important step we have to go and add a header comment at the start of |
| 1:11:23 | each scripts to be honest after 3 months from now you will not be remembering all |
| 1:11:28 | the details of these scripts and adding a comment like this it is like a sticky |
| 1:11:32 | note for you later once you visit this script again and it is as well very |
| 1:11:36 | important for the other developers in the team because each time you open a |
| 1:11:40 | scripts the first question going to be what is the purpose of this script |
| 1:11:44 | because if you or anyone in the team open the file the first question going |
| 1:11:48 | to be what is the purpose of these scripts why we are doing these stuff so |
| 1:11:53 | as you can see here we have a comment saying this scripts create a new data |
| 1:11:56 | warehouse after checking if it already exists if the database exists it's going |
| 1:12:00 | to drop it and recreate it and additionally it's going to go and create |
| 1:12:04 | three schemas bronze silver gold so that it gives Clarity what this script is |
| 1:12:09 | about and it makes everyone life easier now the second reason why this is very |
| 1:12:14 | important to add is that you can add warnings and especially for this script |
| 1:12:19 | it is very important to add these notes because if you run these scripts what's |
| 1:12:22 | going to happen it's going to go and destroy the whole database imagine |
| 1:12:26 | someone open the script and run it imagine an admin open the script and run |
| 1:12:31 | it in your database everything going to be destroyed and all the data will be |
| 1:12:35 | lost and this going to be a disaster if you don't have any backup so with that |
| 1:12:39 | we have nice H our comment and we have added few comments in our codes and now |
| 1:12:43 | we are ready to commit our codes so let's go and commit it and now we have |
| 1:12:49 | our scripts in the git as well and of course if you are doing any |
| 1:12:52 | modifications make sure to update the changes in the Gs okay my friends so |
| 1:12:57 | with that we have an empty database and schemas and we are done with this task |
| 1:13:01 | and as well we are done with the whole epic so we have completed the project |
| 1:13:05 | initialization and now we're going to go to the interesting stuff we will go and |
| 1:13:09 | build the bronze layer so now the first task is to analyze the source systems so |
| 1:13:14 | let's |
| 1:13:17 | go all right so now the big question is how to build the bronze layer so first |
| 1:13:22 | thing first we do analyzing as you are developing anything you don't |
| 1:13:26 | immediately start writing a code so before we start coding the bronze layer |
| 1:13:30 | what we usually do is we have to understand the source system so what I |
| 1:13:34 | usually do I make an interview with the source system experts and ask them many |
| 1:13:38 | many questions in order to understand the nature of the source system that I'm |
| 1:13:43 | connecting to the data warehouse and once you know the source systems then we |
| 1:13:47 | can start coding and the main focus here is to do the data ingestion so that |
| 1:13:52 | means we have to find a way on how to load the data from The Source into the |
| 1:13:56 | data warehouse so it's like we are building a bridge between the source and |
| 1:14:01 | our Target system the data warehouse and once we have the code ready the next |
| 1:14:04 | step is we have to do data validation so here comes the quality control it is |
| 1:14:09 | very important in the bronze layer to check the data completeness so that |
| 1:14:12 | means we have to compare the number of Records between the source system and |
| 1:14:17 | the bronze layer just to make sure we are not losing any data in between and |
| 1:14:21 | another check that we will be doing is the schema checks and that's to make |
| 1:14:24 | sure that the data is placed on the right position and finally we don't have |
| 1:14:28 | to forget about documentation and committing our work in the gits so this |
| 1:14:33 | is the process that we're going to follow to build the bronze |
| 1:14:39 | layer all right my friends so now before connecting any Source systems to our |
| 1:14:43 | data warehouse we have to make very important step is to understand the |
| 1:14:48 | sources so how I usually do it I set up a meeting with the source systems |
| 1:14:52 | experts in order to interview them to ask them a lot of stuff about the source |
| 1:14:56 | and gaining this knowledge is very important because asking the right |
| 1:14:59 | question will help you to design the correct scripts in order to extract the |
| 1:15:03 | data and to avoid a lot of mistakes and challenges and now I'm going to show you |
| 1:15:08 | the most common questions that I usually ask before connecting anything okay so |
| 1:15:12 | we start first by understanding the business context and the ownership so I |
| 1:15:16 | would like to understand the story behind the data I would like to |
| 1:15:19 | understand who is responsible for the data which it departments and so on and |
| 1:15:23 | then it's nice to understand as well what business process it supports does |
| 1:15:27 | it support the customer transactions the supply chain Logistics or maybe Finance |
| 1:15:32 | reporting so with that you're going to understand the importance of your data |
| 1:15:35 | and then I ask about the system and data documentation so having documentations |
| 1:15:40 | from the source is your learning materials about your data and it going |
| 1:15:43 | to saves you a lot of time later when you are working and designing maybe new |
| 1:15:48 | data models and as well I would like always to understand the data model for |
| 1:15:52 | the source system and if they have like descript I of the columns and the tables |
| 1:15:56 | it's going to be nice to have the data catalog this can helps me a lot in the |
| 1:15:59 | data warehouse how I'm going to go and join the tables together so with that |
| 1:16:03 | you get a solid foundations about the business context the processes and the |
| 1:16:07 | ownership of the data and now in The Next Step we're going to start talking |
| 1:16:11 | about the technicality so I would like to understand the architecture and as |
| 1:16:14 | well the technology stack so the first question that I usually ask is how the |
| 1:16:19 | source system is storing the data do we have the data on the on Prem like an SQL |
| 1:16:23 | Server Oracle or is it in the cloud like Azure lws and so on and then once we |
| 1:16:29 | understand that then we can discuss what are the integration capabilities like |
| 1:16:33 | how I'm going to go and get the data do the source system offer apis maybe CFA |
| 1:16:38 | or they have only like file extractions or they're going to give you like a |
| 1:16:42 | direct connection to the database so once you understand the technology that |
| 1:16:46 | you're going to use in order to extract the data then we're going to Deep dive |
| 1:16:49 | into more technical questions and here we can understand how to extract the |
| 1:16:53 | data from The Source system and and then load it into the data warehouse so the |
| 1:16:57 | first things that we have to discuss with the experts can we do an |
| 1:17:00 | incremental load or a full load and then after that we're going to discuss the |
| 1:17:04 | data scope the historization do we need all data do we need only maybe 10 years |
| 1:17:09 | of the data are there history is already in the source system or should we build |
| 1:17:13 | it in the data warehouse and so on and then we're going to go and discuss what |
| 1:17:18 | is the expected size of the extracts are we talking here about megabytes |
| 1:17:22 | gigabytes terabytes and this is very important to understand whether we have |
| 1:17:26 | the right tools and platform to connect the source system and then I try to |
| 1:17:31 | understand whether there are any data volume limitations like if you have some |
| 1:17:34 | Old Source systems they might struggle a lot with performance and so on so if you |
| 1:17:39 | have like an ETL that extracting large amount of data you might bring the |
| 1:17:43 | performance down of the source system so that's why you have to try to understand |
| 1:17:47 | whether there are any limitations for your extracts and as well other aspects |
| 1:17:51 | that might impact the performance of The Source system this is very important if |
| 1:17:55 | they give you an access to the database you have to be responsible that you are |
| 1:17:59 | not bringing the performance of the database down and of course very |
| 1:18:03 | important question is to ask about the authentication and the authorization |
| 1:18:07 | like how you going to go and access the data in the source system do you need |
| 1:18:10 | any tokens Keys password and so on so those are the questions that you have to |
| 1:18:14 | ask if you are connecting new source system to the data warehouse and once |
| 1:18:19 | you have the answers for those questions you can proceed with the next steps to |
| 1:18:23 | connect the sources to the that Warehouse all right my friends so with |
| 1:18:26 | that you have learned how to analyze a new source systems that you want to |
| 1:18:30 | connect to your data warehouse so this STP is done and now we're going to go |
| 1:18:34 | back to coding where we're going to write scripts in order to do the data |
| 1:18:37 | ingestion from the CSV files to the Bros |
| 1:18:43 | layer and let's have quick look again to our bronze layer specifications so we |
| 1:18:48 | just have to load the data from the sources to the data warehouse we're |
| 1:18:52 | going to build tables in the bronze layer we are doing a full load so that |
| 1:18:56 | means we are trating and then inserting the data there will be no data |
| 1:18:59 | Transformations at all in the bronze layer and as well we will not be |
| 1:19:03 | creating any data model so this is the specifications of the bronze layer all |
| 1:19:08 | right now in order to create the ddl script for the bronze layer creating the |
| 1:19:11 | tables of the bronze we have to understand the metadata the structure |
| 1:19:15 | the schema of the incoming data and here either you ask the technical experts |
| 1:19:20 | from The Source system about these informations or you can go and explore |
| 1:19:24 | the incoming data and try to define the structure of your tables so now what |
| 1:19:28 | we're going to do we're going to start with the First Source system the CRM so |
| 1:19:32 | let's go inside it and we're going to start with the first table that customer |
| 1:19:35 | info now if you open the file and check the data inside it you see we have a |
| 1:19:39 | Header information and that is very good because now we have the names of the |
| 1:19:43 | columns that are coming from the source and from the content you can Define of |
| 1:19:47 | course the data types so let's go and do that first we're going to say create |
| 1:19:51 | table and then we have to define the layer it's going to be the bronze and |
| 1:19:55 | now very important we have to follow the naming convention so we start with the |
| 1:19:58 | name of the source system it is the CRM underscore and then after that the table |
| 1:20:03 | name from The Source system so it's going to be the costore info so this is |
| 1:20:08 | the name of our first table in the bronze layer then the next step we have |
| 1:20:11 | to go and Define of course the columns and here again the column names in the |
| 1:20:15 | bronze layer going to be one to one exactly like the source system so the |
| 1:20:20 | first one going to be the ID and I will go with the data type integer then the |
| 1:20:24 | next one going to be the key invar Char and the length I will go with |
| 1:20:31 | [Music] 50 and the last one going to be the |
| 1:20:38 | create dates it's going to be date so with that we have covered all the |
| 1:20:43 | columns available from The Source system so let's go and check and yes the last |
| 1:20:47 | one is the create date so that's it for the first table now semicolon of course |
| 1:20:51 | at the end let's go and execute it and now we're going to go to the object |
| 1:20:54 | Explorer over here refresh and we can see the first table inside our data |
| 1:20:59 | warehouse amazing right so now next what you have to do is to go and create a ddl |
| 1:21:04 | statement for each file for those two systems so for the CRM we need three |
| 1:21:10 | ddls and as well for the other system the Erp we have as well to create three |
| 1:21:15 | ddls for the three files so at the ends we're going to have in the bronze ler |
| 1:21:19 | Six Tables six ddls so now pause the video go create those ddls I will be |
| 1:21:24 | doing the same as well and we will see you |
| 1:21:31 | soon all right so now I hope you have created all those details I'm going to |
| 1:21:34 | show you what I have just created so the second table in the source CRM we have |
| 1:21:39 | the product informations and the third one is the sales details then we go to |
| 1:21:44 | the second system and here we make sure that we are following the naming |
| 1:21:47 | convention so first The Source system Erb and then the table name so the |
| 1:21:52 | second system was really easy you can see we have only here like two columns |
| 1:21:55 | and for the customers like only three and for the categories only four columns |
| 1:22:00 | all right so after defining those stuff of course we have to go and execute them |
| 1:22:04 | so let's go and do that and then we go to the object Explorer over here refresh |
| 1:22:08 | the tables and with that you can see we have six empty tables in the bronze |
| 1:22:13 | layer and with that we have all the tables from the two Source systems |
| 1:22:17 | inside our database but still we don't have any data and you can see our naming |
| 1:22:21 | convention is really nice you see the first three tables comes from the CRM |
| 1:22:26 | Source system and then the other three comes from the Erb so we can see in the |
| 1:22:30 | bronze layer the things are really splitted nicely and you can identify |
| 1:22:34 | quickly which table belonged to which source system now there is something |
| 1:22:38 | else that I usually add to the ddl script is to check whether the table |
| 1:22:42 | exists before creating so for example let's say that you are renaming or you |
| 1:22:46 | would like to change the data type of specific field if you just go and run |
| 1:22:51 | this Square you will get an error because the database going to say we |
| 1:22:54 | have already this table so in other databases you can say create or replace |
| 1:22:58 | table but in the SQL Server you have to go and build a tsql logic so it is very |
| 1:23:03 | simple first we have to go and check whether the object exist in the database |
| 1:23:06 | so we say if object ID and then we have to go and specify the table name so |
| 1:23:12 | let's go and copy the whole thing over here and make sure you get exactly the |
| 1:23:17 | same name as a table name so there is see like space I'm just going to go and |
| 1:23:21 | remove it and then we're going to go and Define the object type so going to be |
| 1:23:24 | the U it stands for user it is the user defined tables so if this table is not |
| 1:23:30 | null so this means the database did find this object in the database so what can |
| 1:23:35 | happen we say go and drop the table so the whole thing again and semicolon so |
| 1:23:42 | again if the table exist in the database is not null then go and drop the table |
| 1:23:47 | and after that go and created so now if you go and highlight the whole thing and |
| 1:23:52 | then execute it it will be working so first drop the table if it exist then go |
| 1:23:57 | and create the table from scratch now what you have to do is to go and add |
| 1:24:01 | this check before creating any table inside our database so it's going to be |
| 1:24:06 | the same thing for the next table and so on I went and added all those checks for |
| 1:24:11 | each table and what can happen if I go and execute the whole thing it going to |
| 1:24:16 | work so with that I'm recreating all the tables in the bronze layer from the |
| 1:24:20 | scratch |
| 1:24:25 | now the methods that we're going to use in order to load the data from the |
| 1:24:28 | source to the data warehouse is the bulk inserts bulk insert is a method of |
| 1:24:33 | loading massive amount of data very quickly from files like CSV files or |
| 1:24:38 | maybe a text file directly into a database it's is not like the classical |
| 1:24:43 | normal inserts where it's going to go and insert the data row by row but |
| 1:24:47 | instead the PK insert is one operation that's going to load all the data in one |
| 1:24:52 | go into the database and that's what makes it very fast so let's go and use |
| 1:24:56 | this methods okay so now let's start writing the script in order to load the |
| 1:25:00 | first table in the source CRM so we're going to go and load the table customer |
| 1:25:04 | info from the CSV file to the database table so the syntax is very simple we're |
| 1:25:09 | going to start to saying pulk insert so with that SQL understand we are doing |
| 1:25:14 | not a normal insert we are doing a pulk insert and then we have to go and |
| 1:25:17 | specify the table name so it is bronze. CRM cost info so now now we have to |
| 1:25:24 | specify the full location of the file that we are trying to load in this table |
| 1:25:29 | so now what we have to do is to go and get the path where the file is stored so |
| 1:25:34 | I'm going to go and copy the whole path and then add it to the P insert exactly |
| 1:25:38 | like where the data exists so for me it is in csql data warehouse project data |
| 1:25:44 | set in the source CRM and then I have to specify the file name so it's going to |
| 1:25:49 | be the costore info. CSV you have to get it exactly like like the path of your |
| 1:25:55 | files otherwise it will not be working so after the path now we come to the |
| 1:25:59 | with CLA now we have to tell the SQL Server how to handle our file so here |
| 1:26:04 | comes the specifications there is a lot of stuff that we can Define so let's |
| 1:26:08 | start with the very important one is the row header now if you check the content |
| 1:26:13 | of our files you can see always the first row includes the Header |
| 1:26:17 | information of the file so those informations are actually not the data |
| 1:26:22 | it's just the column names the ACT data starts from the second row and we have |
| 1:26:27 | to tell the database about this information so we're going to say first |
| 1:26:31 | row is actually the second row so with that we are telling SQL to skip the |
| 1:26:37 | first row in the file we don't need to load those informations because we have |
| 1:26:40 | already defined the structure of our table so this is the first |
| 1:26:44 | specifications the next one which is as well very important and loading any CSV |
| 1:26:49 | file is the separator between Fields the delimiter between Fields so it's really |
| 1:26:54 | depend on the file structure that you are getting from the source as you can |
| 1:26:57 | see all those values are splitted with a comma and we call this comma as a file |
| 1:27:03 | separator or a delimiter and I saw a lot of different csvs like sometime they use |
| 1:27:07 | a semicolon or a pipe or special character like a hash and so on so you |
| 1:27:11 | have to understand how the values are splitted and in this file it's splitted |
| 1:27:15 | by the comma and we have to tell SQL about this info it's very important so |
| 1:27:19 | we going to say fill Terminator and then we're going to say it is the comma and |
| 1:27:25 | basically those two informations are very important for SQL in order to be |
| 1:27:28 | able to read your CSV file now there are like many different options that you can |
| 1:27:33 | go and add for example tabe lock it is an option in order to improve the |
| 1:27:38 | performance where you are locking the entire table during loading it so as SQL |
| 1:27:43 | is loading the data to this table it going to go and lock the whole table so |
| 1:27:48 | that's it for now I'm just going to go and add the semicolon and let's go and |
| 1:27:51 | insert the data from the file inside our pron table let's execute it and now you |
| 1:27:55 | can see SQL did insert around 880,000 rows inside our table so it is working |
| 1:28:00 | we just loaded the file into our data Bas but now it is not enough to just |
| 1:28:04 | write the script you have to test the quality of your bronze table especially |
| 1:28:09 | if you are working with files so let's go and just do a simple select so from |
| 1:28:13 | our new table and let's run it so now the first |
| 1:28:19 | thing that I check is do we have data like in each column well yes as you can |
| 1:28:23 | see we have data and the second thing is do we have the data in the correct |
| 1:28:28 | column this is very critical as you are loading the data from a file to a |
| 1:28:32 | database do we have the data in the correct column so for example here we |
| 1:28:35 | have the first name which of course makes sense and here we have the last |
| 1:28:38 | name but what could happen and this mistakes happens a lot is that you find |
| 1:28:43 | the first name informations inside the key and as well you see the last name |
| 1:28:47 | inside the first name and the status inside the last name so there is like |
| 1:28:51 | shifting of the data and this data engineering mistake is very common if |
| 1:28:55 | you are working with CSV files and there are like different reasons why it |
| 1:28:59 | happens maybe the definition of your table is wrong or the filled separator |
| 1:29:03 | is wrong maybe it's not a comma it's something else or the separator is a bad |
| 1:29:08 | separator because sometimes maybe in the keys or in the first name there is a |
| 1:29:12 | comma and the SQL is not able to split the data correctly so the quality of the |
| 1:29:17 | CSV file is not really good and there are many different reasons why you are |
| 1:29:21 | not getting the data in the correct column but for now everything looks fine |
| 1:29:25 | for us and the next step is that I go and count the rows inside this table so |
| 1:29:31 | let's go and select that so we can see we have |
| 1:29:35 | 18,490 and now what we can do we can go to our CSV file and check how many rows |
| 1:29:39 | do we have inside this file and as you can see we have |
| 1:29:44 | 18,490 we are almost there there is like one extra row inside the file and that's |
| 1:29:49 | because of the header the first Header information is not loaded inside our |
| 1:29:53 | table and that's why always in our tables we're going to have one less row |
| 1:29:57 | than the original files so everything looks nice and we have done this step |
| 1:30:01 | correctly now if I go and run it again what's going to happen we will get dcat |
| 1:30:07 | inside the bronze layer so now we have loaded the file like twice inside the |
| 1:30:11 | same table which is not really correct the method that we have discussed is |
| 1:30:16 | first to make the table empty and then load trate and then insert in order to |
| 1:30:21 | do that before the bulk inserts what we're going to do we're going to say |
| 1:30:25 | truncate table and then we're going to have our |
| 1:30:29 | table and that's it with a semicolon so now what we are doing is first we are |
| 1:30:34 | making the table empty and then we start loading from the scratch we are loading |
| 1:30:39 | the whole content of the file inside the table and this is what we call full load |
| 1:30:44 | so now let's go and Mark everything together and execute and again if you go |
| 1:30:48 | and check the content of the table you can see we have only 18,000 rows let's |
| 1:30:53 | go and run it again the count of the bronze layer you can see we still have |
| 1:30:58 | the 18,000 so each time you run this script now we are refreshing the table |
| 1:31:03 | customer info from the file into the database table so we are refreshing the |
| 1:31:07 | bronze layer table so that means if there is like now any changes in the |
| 1:31:11 | file it will be loaded to the table so this is how you do a full load in the |
| 1:31:16 | bronze layer by trating the table and then doing the inserts and now of course |
| 1:31:21 | what we have to do is to Bow the video and go and write WR the same script for |
| 1:31:25 | all six files so let's go and do |
| 1:31:30 | [Music] that okay back so I hope that you have |
| 1:31:35 | as well written all those scripts so I have the three tables in order to load |
| 1:31:39 | the First Source system and then three sections in order to load the Second |
| 1:31:43 | Source system and as I'm writing those scripts make sure to have the correct |
| 1:31:47 | path so for the Second Source system you have to go and change the path for the |
| 1:31:50 | other folder and as well don't forget the table name on the bronze layer is |
| 1:31:54 | different from the file name because we start always with the source system name |
| 1:31:59 | with the files we don't have that so now I think I have everything is ready so |
| 1:32:03 | let's go and execute the whole thing perfect awesome so everything is working |
| 1:32:08 | let me check the messages so we can see from the message how many rows are |
| 1:32:12 | inserted in each table and now of course the task is to go through each table and |
| 1:32:17 | check the |
| 1:32:21 | content so that means now we have really ni script in order to load the bronze |
| 1:32:26 | layer and we will use this script in daily basis every day we have to run it |
| 1:32:31 | in order to get a new content to the data warehouse and as you learned before |
| 1:32:35 | if you have like a script of SQL that is frequently used what we can do we can go |
| 1:32:40 | and create a stored procedure from those scripts so let's go and do that it's |
| 1:32:45 | going to be very simple we're going to go over here and say create or alter |
| 1:32:49 | procedure and now we have to define the name of the Sol procedure I'm going to |
| 1:32:53 | go and put it in the schema bronze because it belongs to the bronze layer |
| 1:32:58 | so then we're going to go and follow the naming convention the S procedure starts |
| 1:33:02 | with load underscore and then the bronze layer so that's it about the name and |
| 1:33:06 | then very important we have to define the begin and as well the end of our SQL |
| 1:33:10 | statements so here is the beginning and let's go to the end and say this is the |
| 1:33:16 | end and then let's go highlight everything in between and give it one |
| 1:33:20 | push with tab so with that it is easier to read so now next one we're going to |
| 1:33:24 | do we're going to go and execute it so let's go and create this St procedure |
| 1:33:27 | and now if you want to go and check your St procedure you go to the database and |
| 1:33:31 | then we have here folder called programmability and then inside we have |
| 1:33:34 | start procedure so if you go and refresh you will see our new start procedure |
| 1:33:38 | let's go and test it so I'm going to go and have new query and what we're going |
| 1:33:42 | to do we're going to say execute bronze. load bronze so let's go and execute it |
| 1:33:48 | and with that we have just loaded completely the pron layer so as you can |
| 1:33:53 | see SQL did go and insert all the data from the files to the bronze layer it is |
| 1:33:57 | way easier than each time running those scripts of course all right so now the |
| 1:34:01 | next step is that as you can see the output message it is really not having a |
| 1:34:06 | lot of informations the message of your ETL with s procedure it will not be |
| 1:34:10 | really clear so that's why if you are writing an ETL script always take care |
| 1:34:15 | of the messaging of your code so let me show you a nice design let's go back to |
| 1:34:19 | our St procedure so now what we can do we can go and divide the message p based |
| 1:34:24 | on our code so now we can start with a message for example over here let's say |
| 1:34:27 | print and we say what you are doing with this thir procedure we are loading the |
| 1:34:32 | bronze ler so this is the main message the most important one and we can go and |
| 1:34:37 | play with the separators like this so we can say print and now we can go and add |
| 1:34:41 | some nice separators like for example the equals at the start and at the end |
| 1:34:46 | just to have like a section so this is just a nice message at the start so now |
| 1:34:50 | by looking to our code we can see that our code is splited into two sections |
| 1:34:54 | the first section we are loading all the tables from The Source system CRM and |
| 1:34:59 | the second section is loading the tables from the Erp so we can split the prints |
| 1:35:04 | by The Source system so let's go and do that so we're going to say print and |
| 1:35:08 | we're going to say loading CRM tables this is for the first section and then |
| 1:35:13 | we can go and add some nice separators like the one let's take the minus and of |
| 1:35:19 | course don't forget to add semicolons like me so we can to have semicolon |
| 1:35:24 | for each print same thing over here I will go and copy the whole thing because |
| 1:35:29 | we're going to have it at the start and as well at the end let's go copy the |
| 1:35:32 | whole thing for the second section so for the Erp it starts over here and |
| 1:35:37 | we're going to have it like this and we're going to call it loading Erp so |
| 1:35:41 | with that in the output we can see nice separation between loading each Source |
| 1:35:45 | system now we go to the next step where we go and add like a print for each |
| 1:35:50 | action so for example here we are Tran getting the table so we say print and |
| 1:35:55 | now what we can do we can go and add two arrows and we say what we are doing so |
| 1:35:59 | we are trating the table and then we can go and add the table name in the message |
| 1:36:04 | as well so this is the first action that we are doing and we can go and add |
| 1:36:08 | another print for inserting the data so we can say inserting data into and then |
| 1:36:15 | we have the table name so with that in the output we can understand what SQL is |
| 1:36:19 | doing so let's go and repeat this for all other tables Okay so I just added |
| 1:36:24 | all those prints and don't forget the semicolon at the end so I would say |
| 1:36:28 | let's go and execute it and check the output so let's go and do that and then |
| 1:36:32 | maybe at the start just to have quick output execute our stored procedure like |
| 1:36:37 | this so let's see now if you check the output you can see things are more |
| 1:36:42 | organized than before so at the start we are reading okay we are loading the |
| 1:36:45 | bronze layer now first we are loading the source system CRM and then the |
| 1:36:50 | second section is for the Erp and we can see the actions so we trating inserting |
| 1:36:54 | trating inserting for each table and as well the same thing for the Second |
| 1:36:58 | Source so as you can see it is nice and cosmetic but it's very important as you |
| 1:37:03 | are debugging any errors and speaking of Errors we have to go and handle the |
| 1:37:07 | errors in our St procedure so let's go and do that it's going to be the first |
| 1:37:12 | thing that we do we say begin try and then we go to the end of our scripts and |
| 1:37:17 | we say before the last end we say end try and then the next thing we have to |
| 1:37:22 | add the catch so we're going to say begin catch and end catch so now first |
| 1:37:28 | let's go and organize our code I'm going to take the whole codes and give it one |
| 1:37:34 | more push and as well the begin try so it is more organized and as you know the |
| 1:37:39 | try and catch is going to go and execute the try and if there is like any errors |
| 1:37:44 | during executing this script the second section going to be executed so the |
| 1:37:49 | catch will be executed only if the SQL failed to run that try so now what we |
| 1:37:54 | have to do is to go and Define for SQL what to do if there's like an error in |
| 1:37:58 | your code and here we can do multiple stuff like maybe creating a logging |
| 1:38:02 | tables and add the messages inside this table or we can go and add some nice |
| 1:38:07 | messaging to the output like very example we can go and add like a section |
| 1:38:11 | again over here so again some equals and we can go and repeat it over here and |
| 1:38:17 | then add some content in between so we can start with something like to say |
| 1:38:21 | error Accord during loading bronze layer and then we |
| 1:38:27 | can go and add many stuff like for example we can go and add the error |
| 1:38:33 | message and here we can go and call the function |
| 1:38:36 | error message and we can go and add as well for example the error number so |
| 1:38:42 | error number and of course the output of this going to be in number but the error |
| 1:38:47 | message here is a text so we have to go and change the data type so we're going |
| 1:38:51 | to do a cast as in VAR Char like this and then there is like many functions |
| 1:38:57 | that you can add to the output like for example the error States and so on so |
| 1:39:02 | you can design what can happen if there is an error in the ETL now what else is |
| 1:39:06 | very important in each ETL process is to add the duration of each like step so |
| 1:39:12 | for example I would like to understand how long it takes to load this table |
| 1:39:16 | over here but looking to the output I don't have any informations how long is |
| 1:39:20 | taking to load my tables and this is very important because because as you |
| 1:39:24 | are building like a big data warehouse the ATL process is going to take long |
| 1:39:28 | time and you would like to understand where is the issue where is the |
| 1:39:31 | bottleneck which table is consuming a lot of time to be loaded so that's why |
| 1:39:35 | we have to add those informations as well to the output or even maybe to |
| 1:39:39 | protocol it in a table so let's go and add as well this step so we're going to |
| 1:39:43 | go to the start and now in order to calculate the duration you need the |
| 1:39:47 | starting time and the end time so we have to understand when we started |
| 1:39:51 | loaded and when we ended loading the table so now the first thing is we have |
| 1:39:55 | to go and declare the variables so we're going to say declare and then let's make |
| 1:40:00 | one called start time and the data type of this going to be the date time I need |
| 1:40:04 | exactly the second when it started and then another one for the end time so |
| 1:40:10 | another variable end time and as well the same thing date time so with that we |
| 1:40:14 | have declared the variables and the next step is to go and use them so now let's |
| 1:40:18 | go to the first table to the customer info and at the start we're going to say |
| 1:40:23 | set start |
| 1:40:24 | time equal to get date so we will get the exact time when we start loading |
| 1:40:31 | this table and then let's go and copy the whole thing and go to the end of |
| 1:40:34 | loading over here so we're going to say set this time the end time equal as well |
| 1:40:40 | to the get dates so with that now we have the values of when we start loading |
| 1:40:45 | this table and when we completed loading the table and now the next step is we |
| 1:40:49 | have to go and print the duration those informations so over here we can go and |
| 1:40:54 | say print and we can go and have as again the same design so two arrows and |
| 1:40:58 | we can say very simply load duration and then double points and space and now |
| 1:41:04 | what we have to do is to calculate the duration and we can do that using the |
| 1:41:08 | date and time function date diff in order to find the interval between two |
| 1:41:13 | dates so we're going to say plus over here and then use date diff and here we |
| 1:41:17 | have to Define three arguments first one is the unit so you can Define second |
| 1:41:21 | minute hours and so on so we're going to go with a second and then we're going to |
| 1:41:24 | define the start of the interval it's going to be the start time and then the |
| 1:41:28 | last argument is going to be the end of the boundary it's going to be the end |
| 1:41:32 | time and now of course the output of this going to be in number that's why we |
| 1:41:35 | have to go and cast it so we're going to say cast as enar Char and then we're |
| 1:41:40 | going to close it like this and maybe at the ends we're going to say plus space |
| 1:41:46 | seconds in order to have a nice message so again what we have done we have |
| 1:41:49 | declared the two variables and we are using them at the start we we are |
| 1:41:53 | getting the current date and time and at the end of loading the table we are |
| 1:41:57 | getting the current date and time and then we are finding the differences |
| 1:42:01 | between them in order to get the load duration and in this case we are just |
| 1:42:05 | priting this information and now we can go of course and add some nice separator |
| 1:42:09 | between each table so I'm going to go and do it like this just few minuses not |
| 1:42:14 | a lot of stuff so now what we have to do is to go and add this mechanism for each |
| 1:42:19 | table in order to measure the speed of the ETL for each one of |
| 1:42:24 | [Music] |
| 1:42:28 | them okay so now I have added all those configurations for each table and let's |
| 1:42:34 | go and run the whole thing now so let's go and edit the stor procedure this and |
| 1:42:40 | we're going to go and run it so let's go and execute so now as you can see we |
| 1:42:44 | have here one more info about the load durations and it is everywhere I can see |
| 1:42:49 | we have zero seconds and that's because it is super fast of loading those |
| 1:42:53 | informations we are doing everything locally at PC so loading the data from |
| 1:42:57 | files to database going to be Mega fast but of course in real projects you have |
| 1:43:02 | like different servers and networking between them and you have millions of |
| 1:43:05 | rods in the tables of course the duration going to be not like 0 seconds |
| 1:43:10 | things going to be slower and now you can see easily how long it takes to load |
| 1:43:14 | each of your tables and now of course what is very interesting is to |
| 1:43:18 | understand how long it takes to load the whole pron lier so now your task is is |
| 1:43:23 | as well to print at the ends informations about the whole patch how |
| 1:43:27 | long it took to load the bronze |
| 1:43:32 | [Music] layer okay I hope we are done now I have |
| 1:43:37 | done it like this we have to Define two new variables so the start time of the |
| 1:43:42 | batch and the end time of the batch and the first step in the start procedure is |
| 1:43:46 | to get that date and time informations for the first variable and exactly at |
| 1:43:51 | the end the last thing that we do in the start procedure we're going to go and |
| 1:43:55 | get the date and time informations for the end time so we say again set get |
| 1:44:01 | date for the patch in time and then all what you have to do is to go and print a |
| 1:44:05 | message so we are saying loading bronze layer is completed and then we are |
| 1:44:09 | printing total load duration and the same thing with a date difference |
| 1:44:13 | between the patch start time and the end time and we are calculating the seconds |
| 1:44:17 | and so on so now what you have to do is to go and execute the whole thing so |
| 1:44:21 | let's go and refresh the definition of the S procedure and then let's go and |
| 1:44:26 | execute it so in the output we have to go to the last message and we can see |
| 1:44:30 | loading pron layer is completed and the total load duration is as well 0 seconds |
| 1:44:35 | because the execution time is less than 1 seconds so with that you are getting |
| 1:44:40 | now a feeling about how to build an ETL process so as you can see the data |
| 1:44:44 | engineering is not all about how to load the data it's how to engineer the whole |
| 1:44:49 | pipeline how to measure the speed of loading the data what can happen happen |
| 1:44:53 | if there's like an error and to print each step in your ETL process and make |
| 1:44:58 | everything organized and cleared in the output and maybe in the logging just to |
| 1:45:02 | make debugging and optimizing the performance way easier and there is like |
| 1:45:06 | a lot of things that we can add we can add the quality measures and stuff so we |
| 1:45:11 | can add many stuff to our ETL scripts to make our data warehouse professional all |
| 1:45:16 | right my friends so with that we have developed a code in order to load the |
| 1:45:19 | pron layer and we have tested that as well and now in the next step we we're |
| 1:45:23 | going to go back to draw because we want to draw a diagram about the data flow so |
| 1:45:27 | let's |
| 1:45:31 | go so now what is a data flow diagram we're going to draw a Syle visual in |
| 1:45:35 | order to map the flow of your data where it come froms and where it ends up so we |
| 1:45:41 | want just to make clear how the data flows through different layers of your |
| 1:45:45 | projects and that's help us to create something called the data lineage and |
| 1:45:49 | this is really nice especially if you are analyzing an issue so if you have |
| 1:45:53 | like multiple layers and you don't have a real data lineage or flow it's going |
| 1:45:57 | to be really hard to analyze the scripts in order to understand the origin of the |
| 1:46:01 | data and having this diagram going to improve the process of finding issues so |
| 1:46:06 | now let's go and create one okay so now back to draw and we're going to go and |
| 1:46:10 | build the flow diagram so we're going to start first with the source system so |
| 1:46:14 | let's build the layer I'm going to go and remove the fill dotted and then |
| 1:46:19 | we're going to go and add like a box saying sources and we're going to put it |
| 1:46:23 | over here increase the size 24 and as well without any lines now what do we |
| 1:46:30 | have inside the sources we have like folder and files so let's go and search |
| 1:46:35 | for a folder icon I'm going to go and take this one over here and say you are |
| 1:46:39 | the CRM and we can as well increase the size and we have another source we have |
| 1:46:45 | the Erp okay so this is the first layer |
| 1:46:49 | let's go and now have the bronze layer so we're going to go and grab another |
| 1:46:53 | box and we're going to go and make the coloring like this and instead of Auto |
| 1:46:58 | maybe take the hatch maybe something like this whatever you know so rounded |
| 1:47:03 | and then we can go and put on top of it like the title so we can say you are the |
| 1:47:09 | bronze layer and increase as well the size of the font so now what you're |
| 1:47:14 | going to do we're going to go and add boxes for each table that we have in the |
| 1:47:18 | bronze layer so for example we have the sales details we can go and make it |
| 1:47:22 | little bit smaller so maybe 16 and not bold and we have other two tables from |
| 1:47:28 | the CRM we have the customer info and as well the product info so those are the |
| 1:47:35 | three tables that comes from the CRM and now what we're going to do we're going |
| 1:47:38 | to go and connect now the source CRM with all three tables so what we going |
| 1:47:44 | to do we're going to go to the folder and start making arrows from the folder |
| 1:47:48 | to the bronze layer like this and now we have to do the same thing for the Erp |
| 1:47:54 | source so as you can see the data flow diagram shows us in one picture the data |
| 1:47:59 | lineage between the two layers so here we can see easily those three tables |
| 1:48:03 | actually comes from the CRM and as well those three tables in the bronze layer |
| 1:48:07 | are coming from the Erp I understand if we have like a lot of tables it's going |
| 1:48:11 | to be a huge Miss but if you have like small or medium data warehouse building |
| 1:48:16 | those diagrams going to make things really easier to understand how |
| 1:48:19 | everything is Flowing from the sources into the different layers in your data |
| 1:48:24 | warehouse all right so with that we have the first version of the data flow so |
| 1:48:28 | this step is done and the final step is to commit our code in the get |
| 1:48:36 | repo okay so now let's go and commit our work since it is scripts we're going to |
| 1:48:40 | go to the folder scripts and here we're going to have like scripts for the |
| 1:48:43 | bronze silver and gold that's why maybe it makes sense to create a folder for |
| 1:48:47 | each layer so let's go and start creating the bronze folder so I'm going |
| 1:48:51 | to go and create a new file and then I'm going to say pron slash and then we can |
| 1:48:55 | have the DL script of the pron layer dot SQL so now I'm going to go and paste the |
| 1:49:01 | edal codes that we have created so those six tables and as usual at the start we |
| 1:49:06 | have a comment where we are explaining the purpose of these scripts so we are |
| 1:49:09 | saying these scripts creates tables in the pron schema and by running the |
| 1:49:13 | scripts you are redefining the DL structure of the pron tables so let's |
| 1:49:18 | have it like that and I'm going to go and commit the changes all right so now |
| 1:49:22 | as you can see inside the scripts we have a folder called bronze and inside |
| 1:49:27 | it we have the ddl script for the bronze layer and as well in the pron layer |
| 1:49:31 | we're going to go and put our start procedure so we're going to go and |
| 1:49:34 | create a new file let's call it proc load bronze. SQL and then let's go and |
| 1:49:40 | paste our scripts and as usual I have put it at the start an explanation about |
| 1:49:45 | the sord procedure so we are seeing this St procedure going to go and load the |
| 1:49:48 | data from the CSV files into the pron schema so it going go and truncate first |
| 1:49:53 | the tables and then do a pulk inserts and about the parameters this s |
| 1:49:58 | procedure does not accept any parameter or return any values and here a quick |
| 1:50:02 | example how to execute it all right so I think I'm happy with that so let's go |
| 1:50:07 | and commit it all right my friends so with that we have committed our code |
| 1:50:12 | into the gch and with that we are done building the pron layer so the whole is |
| 1:50:17 | done now we're going to go to the next one this one going to be more advanced |
| 1:50:21 | than the bronze layer because the there will be a lot of struggle with cleaning |
| 1:50:24 | the data and so on so we're going to start with the first task where we're |
| 1:50:26 | going to analyze and explore the data in the source systems so let's |
| 1:50:34 | go okay so now we're going to start with the big question how to build the silver |
| 1:50:38 | layer what is the process okay as usual first things first we have to analyze |
| 1:50:43 | and now the task before building anything in the silver layer we have to |
| 1:50:46 | go and explore the data in order to understand the content of our sources |
| 1:50:51 | once we have it what we're going to do we will be starting coding and here the |
| 1:50:54 | transformation that we're going to do is data cleansing this is usually process |
| 1:50:58 | that take really long time and I usually do it in three steps the first step is |
| 1:51:03 | to check first the data quality issues that we have in the pron layer so before |
| 1:51:07 | writing any data Transformations first we have to understand what are the |
| 1:51:10 | issues and only then I start writing data transformations in order to fix all |
| 1:51:16 | those quality issues that we have in the bronze and the last step once I have |
| 1:51:20 | clean results what we're going to do we're going to go and inserted into the |
| 1:51:23 | silver layer and those are the three faces that we will be doing as we are |
| 1:51:27 | writing the code for the silver layer and the third step once we have all the |
| 1:51:31 | data in the server layer we have to make sure that the data is now correct and we |
| 1:51:35 | don't have any quality issues anymore and if you find any issues of course |
| 1:51:38 | what you going to do we're going to go back to coding we're going to do the |
| 1:51:41 | data cleansing and again check so it is like a cycle between validating and |
| 1:51:45 | coding once the quality of the silver layer is good we cannot skip the last |
| 1:51:50 | phase where we going to document and commit our work in the Gs and here we're |
| 1:51:53 | going to have two new documentations we're going to build the data flow |
| 1:51:57 | diagram and as well the data integration diagram after we understood the |
| 1:52:01 | relationship between the sources from the first step so this is the process |
| 1:52:05 | and this is how we going to build the server |
| 1:52:11 | layer all right so now exploring the data in the pron layer so why it is very |
| 1:52:15 | important because understanding the data it is the key to make smart decisions in |
| 1:52:20 | the server layer it was not the focus in the BR layer to understand the content |
| 1:52:24 | of the data at all we focused only how to get the data to the data warehouse so |
| 1:52:29 | that's why we have now to take a moment in order to explore and understand the |
| 1:52:33 | tables and as well how to connect them what are the relationship between these |
| 1:52:37 | tables and it is very important as you are learning about a new source system |
| 1:52:42 | is to create like some kind of documentation so now let's go and |
| 1:52:45 | explore the sources okay so now let's go and explore them one by one we can start |
| 1:52:49 | with the first one from the CRM we have the customer info so right click on it |
| 1:52:53 | and say select top thousand rows and this is of course important if you have |
| 1:52:57 | like a lot of data don't go and explore millions of rows always limit your |
| 1:53:01 | queries so for example here we are using the top thousands just to make sure that |
| 1:53:04 | you are not impacting the system with your queries so now let's have a look to |
| 1:53:07 | the content of this table so we can see that we have here customer informations |
| 1:53:12 | so we have an ID we have a key for the customer we have first name last name my |
| 1:53:16 | Ral status gender and the creation date of the customer so simply this is a |
| 1:53:21 | table for the customer customer information and a lot of details for the |
| 1:53:25 | customers and here we have like two identifiers one it is like technical ID |
| 1:53:29 | and another one it's like the customer number so maybe we can use either the ID |
| 1:53:34 | or the key in order to join it with other tables so now what I usually do is |
| 1:53:38 | to go and draw like data model or let's say integration model just to document |
| 1:53:43 | and visual what I am understanding because if you don't do that you're |
| 1:53:46 | going to forget it after a while so now we go and search for a shape let's |
| 1:53:50 | search for table and I'm going to go and pick this one over here so here we can |
| 1:53:54 | go and change the style for example we can make it rounded or you can go make |
| 1:53:58 | it sketch and so on and we can go and change the color so I'm going to make it |
| 1:54:02 | blue then go to the text make sure to select the whole thing and let's make it |
| 1:54:08 | bigger 26 and then what I'm going to do for those items I'm just going to select |
| 1:54:12 | them and go to arrange and maybe make it 40 something like this so now what we're |
| 1:54:17 | going to do we're going to just go and put the table name so this is the one |
| 1:54:21 | that we are now learning about and what I'm going to do I'm just going to go and |
| 1:54:25 | put here the primary key I will not go and list all the informations so the |
| 1:54:29 | primary key was the ID and I will go and remove all those stuff I don't need it |
| 1:54:34 | now as you can see the table name is not really friendly so I can go and bring a |
| 1:54:38 | text and put it here on top and say this is the customer information just to make |
| 1:54:44 | it friendly and do not forget about it and as well going to increase the size |
| 1:54:48 | to maybe 20 something like this okay with that we have our first table and |
| 1:54:53 | we're going to go and keep exploring so let's move to the second one we're going |
| 1:54:56 | to take the product information right click on it and select the top thousand |
| 1:55:01 | rows I will just put it below the previous query query it now by looking |
| 1:55:06 | to this table we can see we have product informations so we have here a primary |
| 1:55:10 | key for the product and then we have like key or let's say product number and |
| 1:55:14 | after that we have the full name of the product the product costs and then we |
| 1:55:18 | have the product line and then we have like start and end |
| 1:55:22 | well this is interesting to understand why we have start and ends let's have a |
| 1:55:26 | look for example for those three rows all of those three having the same key |
| 1:55:31 | but they have different IDs so it is the same product but with different costs so |
| 1:55:37 | for 2011 we have the cost of 12 then 2012 we have 14 and for the last year |
| 1:55:44 | 2013 we have 13 so it's like we have like a history for the changes so this |
| 1:55:49 | table not only holding the current affirmations of the product but also |
| 1:55:53 | history informations of the products and that's why we have those two dates start |
| 1:55:58 | and end now let's go back and draw this information over here so I'm just going |
| 1:56:02 | to go and duplicate it so the name of this table going to be the BRD info and |
| 1:56:06 | let's go and give it like a short description current and history products |
| 1:56:12 | information something like this just to not forget that we have history in this |
| 1:56:16 | table and here we have as well the PRD ID and there is like nothing that we can |
| 1:56:21 | use in order to join those two tables we don't have like a customer ID here or in |
| 1:56:26 | the other table we don't have any product ID okay so that's it for this |
| 1:56:29 | table let's jump to the third table and the last one in the CRM so let's go and |
| 1:56:34 | select I just made other queries as well short so let's go and execute so what do |
| 1:56:38 | you have over here we have a lot of informations about the order the sales |
| 1:56:42 | and a lot of measures order number we have the product key so this is |
| 1:56:46 | something that we can use in order to join it with the product table we have |
| 1:56:50 | the customer ID we don't have the customer key so here we have like ID and |
| 1:56:55 | here we have key so there's like two different ways on how to join tables and |
| 1:56:59 | then we have here like dates the order dates the shipping date the due date and |
| 1:57:04 | then we have the sales amount the quantity and the price so this is like |
| 1:57:08 | an event table it is transactional table about the orders and sales and it is |
| 1:57:13 | great table in order to connect the customers with the products and as well |
| 1:57:18 | with the orders so let's document this new information that we have so the |
| 1:57:22 | table name is the sales details so we can go and describe it like this |
| 1:57:27 | transactional records about sales and orders and now we have to go and |
| 1:57:35 | describe how we can connect this table to the other two so we are not using the |
| 1:57:39 | product ID we are using the product key and now we need a new column over here |
| 1:57:44 | so you can hold control and enter or you can go over here and add a new row and |
| 1:57:49 | the other row is going to be the customer ID so now for the the customer |
| 1:57:52 | ID it is easy we can gr and grab an arrow in order to connect those two |
| 1:57:56 | tables but for the product key we are not using the ID so that's why I'm just |
| 1:58:01 | going to go and remove this one and say product key let's have here again a |
| 1:58:04 | check so this is a product key it's not a product ID and if we go and check the |
| 1:58:09 | old table the products info you can see we are using this key and not the |
| 1:58:14 | primary key so what we're going to do now we will just go and Link it like |
| 1:58:18 | this and maybe switch those two tables so I will put the customer below just |
| 1:58:23 | perfect it looks nice okay so let's keep moving let's go now to the other source |
| 1:58:27 | system we have the Erp and the first one is ARB cost and we have this cryptical |
| 1:58:32 | name let's go and select the data so now here it's small table and we have only |
| 1:58:37 | three informations so we have here something called C and then we have |
| 1:58:41 | something I think this is the birthday and the gender information so we have |
| 1:58:45 | here male female and so on so it looks again like the customer informations but |
| 1:58:49 | here we have like extra data about the birthday and now if you go and compare |
| 1:58:53 | it to the customer table that we have from the other source system let's go |
| 1:58:57 | and query it you can see the new table from the Erb don't have IDs it has |
| 1:59:02 | actually the customer number or the key so we can go and join those two tables |
| 1:59:07 | using the customer key let's go and document this information so I will just |
| 1:59:11 | go and copy paste and put it here on the right side I will just go and change the |
| 1:59:15 | color now since we are now talking about different Source system and here the |
| 1:59:19 | table name going to be this one and the key called C ID now in order to join |
| 1:59:25 | this table with the customer info we cannot join it with the customer ID we |
| 1:59:29 | need the customer key that's why here we have to go and add a new row so contrl |
| 1:59:33 | enter and we're going to say customer key and then we have to go and make a |
| 1:59:37 | nice Arrow between those two keys so we're going to go and give it a |
| 1:59:41 | description customer information and here we have the birth |
| 1:59:47 | dates okay so now let's keep going we're going to go to the next one we have the |
| 1:59:53 | Erp location let's go and query this table so what do you have over here we |
| 1:59:58 | have the CID again and as you can see we have country informations and this is of |
| 2:00:02 | course again the customer number and we have only this information the country |
| 2:00:07 | so let's go and docment this information this is the customer location table name |
| 2:00:12 | going to be like this and we still have the same ID so we have here still the |
| 2:00:16 | customer ID and we can go and join it using the customer key and we have to |
| 2:00:20 | give it the description locate of customers and we can say here the |
| 2:00:25 | country okay so now let's go to the last table and explore it we have the Erp PX |
| 2:00:32 | catalog so let's go and query those informations so what do we have here we |
| 2:00:37 | have like an ID a category a subcategory and the maintenance here we have like |
| 2:00:43 | either yes and no so by looking to this table we have all the categories and the |
| 2:00:47 | subcategories of the products and here we have like special identifier for |
| 2:00:52 | those informations now the question is how to join it so I would like to join |
| 2:00:56 | it actually with the product informations so let's go and check those |
| 2:01:00 | two tables together okay so in the products we don't have any ID for the |
| 2:01:03 | categories but we have these informations actually in the product key |
| 2:01:08 | so the first five characters of the product key is actually the category ID |
| 2:01:13 | so we can use this information over here in order to join it with the categories |
| 2:01:18 | so we can go and describe this information like this and then we have |
| 2:01:22 | to go and give it a name and then here we have the ID and the ID could be |
| 2:01:26 | joined using the product key so that means for the product information we |
| 2:01:31 | don't need at all the product ID the primary key all what we need is the |
| 2:01:36 | product key or the product number and what I would like to do is like to group |
| 2:01:39 | those informations in a box so let's go grab like any boxes here on the left |
| 2:01:45 | side and make it bigger and then make the edges a little bit smaller let's |
| 2:01:51 | remove move the fill and the line I will make a dotted line and then let's grab |
| 2:01:56 | another box over here and say this is the CRM and we can go and increase the |
| 2:02:01 | size maybe something like 40 smaller 35 bold and change the color to Blue and |
| 2:02:07 | just place it here on top of this box so with that we can understand all those |
| 2:02:11 | tables belongs to the source system CRM and we can do the same stuff for the |
| 2:02:16 | right side as well now of course we have to go and add the description here so |
| 2:02:21 | it's going to be the product categories all right so with that we |
| 2:02:25 | have now clear understanding how the tables are connected to each others we |
| 2:02:30 | understand now the content of each table and of course it can to help us to clean |
| 2:02:34 | up the data in the silver layer in order to prepare it so as you can see it is |
| 2:02:38 | very important to take time understanding the structure of the |
| 2:02:42 | tables the relationship between them before start writing any code all right |
| 2:02:46 | so with that we have now clear understanding about the sources and with |
| 2:02:49 | that we have as well created a data integration in the dro so with that we |
| 2:02:54 | have more understanding about how to connect the sources and now in the next |
| 2:02:58 | two task we will go back to SQL where we're going to start checking the |
| 2:03:01 | quality and as well doing a lot of data Transformations so let's |
| 2:03:08 | go okay so now let's have a quick look to the specifications of the server |
| 2:03:12 | layer so the main objective to have clean and standardized data we have to |
| 2:03:17 | prepare the data before going to the gold layer and we will be building |
| 2:03:21 | tables inside the silver layer and the way of loading the data from the bronze |
| 2:03:25 | to the silver is a full load so that means we're going to trate and then |
| 2:03:29 | insert and here we're going to have a lot of data Transformations so we're |
| 2:03:32 | going to clean the data we're going to bring normalizations standardizations |
| 2:03:36 | we're going to derive new columns we will be doing as well data enrichment so |
| 2:03:40 | a lot of things to be done in the data transformation but we will not be |
| 2:03:44 | building any new data model so those are the specifications and we have to commit |
| 2:03:48 | ourself to this scope okay so now building the ddl script for the layer |
| 2:03:52 | going to be way easier than the bronze because the definition and the structure |
| 2:03:56 | of each table in the silver going to be identical to the bronze layer we are not |
| 2:04:01 | doing anything new so all what you have to do is to take the ddl script from the |
| 2:04:05 | bronze layer and just go and search and replace for the schema I'm just using |
| 2:04:09 | the notepad++ for the scripts so I'm going to go over here and say replace |
| 2:04:13 | the bronze dots with silver dots and I'm going to go and replace all so with that |
| 2:04:19 | now all the ddl is targeting the schema silver layer which is exactly what we |
| 2:04:24 | need all right now before we execute our new ddl script for the silver we have to |
| 2:04:29 | talk about something called the metadata columns they are additional columns or |
| 2:04:33 | fields that the data Engineers add to each table that don't come directly from |
| 2:04:38 | the source systems but the data Engineers use it in order to provide |
| 2:04:42 | extra informations for each record like we can add a column called create date |
| 2:04:47 | is when the record was loaded or an update date when the the record got |
| 2:04:52 | updated or we can add the source system in order to understand the origin of the |
| 2:04:57 | data that we have or sometimes we can add the file location in order to |
| 2:05:02 | understand the lineage from which file the data come from those are great tool |
| 2:05:06 | if you have data issue in your data warehouse if there is like corrupt data |
| 2:05:10 | and so on this can help you to track exactly where this issue happens and |
| 2:05:15 | when and as well it is great in order to understand whether I have Gap in my data |
| 2:05:20 | especially if you are doing incremental mod it is like putting labels on |
| 2:05:23 | everything and you will thank yourself later when you start using them in hard |
| 2:05:28 | times as you have an issue in your data warehouse so now back to our ddl scripts |
| 2:05:32 | and all what you have to do is to go and do the following so for example for the |
| 2:05:35 | first table I will go and add at the end one more extra column so it start with |
| 2:05:41 | the prefix DW as we have defined in the naming convention and then underscore |
| 2:05:46 | let's have the create dates and the data tabe going to be date time to and now |
| 2:05:51 | what we can do is we can go and add a default value for it I want the database |
| 2:05:55 | to generate these informations automatically we don't have to specify |
| 2:05:59 | that in any ETL scripts so which value it's going to be the get datee so each |
| 2:06:04 | record going to be inserted in this table will get automatically a value |
| 2:06:08 | from the current date and time so now as you can see the naming convention it is |
| 2:06:12 | very important all those columns comes from the source system and only this one |
| 2:06:16 | column comes from the data engineer of the data warehouse okay so that's it |
| 2:06:20 | let's go and repeat the same thing for all other tables so I will just go and |
| 2:06:24 | add this piece of information for each ddl all right so I think that's it all |
| 2:06:32 | what you have to do is now to go and execute the whole ddl script for the |
| 2:06:36 | silver layer let's go into that all right perfect there's no errors let's go |
| 2:06:40 | and refresh the tables on the object Explorer and with that as you can see we |
| 2:06:44 | have six tables for the silver layer it is identical to the bronze layer but we |
| 2:06:48 | have one extra column for the metadata |
| 2:06:55 | all right so now in the server layer before we start writing any data |
| 2:06:58 | Transformations and cleansing we have first to detect the quality issues in |
| 2:07:03 | the pron without knowing the issues we cannot find solution right we will |
| 2:07:07 | explore first the quality issues only then we start writing the transformation |
| 2:07:12 | scripts so let's [Music] |
| 2:07:19 | go okay so now what we're going to do we're going to go through all the tables |
| 2:07:23 | over the bronze layer clean up the data and then insert it to the server layer |
| 2:07:27 | so let's start with the first table the first bronze table from The Source CRM |
| 2:07:32 | so we're going to go to the bronze CRM customer info so let's go and query the |
| 2:07:37 | data over here now of course before writing any data and Transformations we |
| 2:07:41 | have to go and detect and identify the quality issues of this table so usually |
| 2:07:46 | I start with the first check where we go and check the primary key so we have to |
| 2:07:51 | go and check whether there are nulls inside the primary key and whether there |
| 2:07:54 | are duplicates so now in order to detect the duplicates in the primary key what |
| 2:07:58 | we have to do is to go and aggregate the primary key if we find any value in the |
| 2:08:03 | primary key that exist more than once that means it is not unique and we have |
| 2:08:07 | duplicates in the table so let's go and write query for that so what we're going |
| 2:08:11 | to do we're going to go with the customer ID and then we're going to go |
| 2:08:14 | and count and then we have to group up the data so Group by based on the |
| 2:08:19 | primary key and of course we don't need all the results we need only where we |
| 2:08:23 | have an issue so we're going to say having |
| 2:08:27 | counts higher than one so we are interested in the values where the count |
| 2:08:32 | is higher than one so let's go and execute it now as you can see we have |
| 2:08:36 | issue in this table we have duplicates because all those IDs exist more than |
| 2:08:41 | one in the table which is completely wrong we should have the primary key |
| 2:08:44 | unique and you can see as well we have three records where the primary key is |
| 2:08:48 | empty which is as well a bad thing now there is an issue here if we have only |
| 2:08:53 | one null it will not be here at the result so what I'm going to do I'm going |
| 2:08:56 | to go over here and say or the primary key is null just in case if we have only |
| 2:09:03 | one null I'm still interested to see the results so if I go and run it again |
| 2:09:07 | we'll get the same results so this is equality check that you can do on the |
| 2:09:11 | table and as you can see it is not meeting the expectation so that means we |
| 2:09:15 | have to do something about it so let's go and create a new query so here what |
| 2:09:19 | we're going to do we can to start writing the query that is doing the data |
| 2:09:22 | transformation and the data cleansing so let's start again by selecting the |
| 2:09:28 | [Music] data and excuse it again so now what I |
| 2:09:33 | usually do I go and focus on the issue so for example let's go and take one of |
| 2:09:38 | those values and I focus on it before start writing the transformation so |
| 2:09:42 | we're going to say where customer ID equal to this value all right so now as |
| 2:09:47 | you can see we have here the issue where the ID exist three times but actually we |
| 2:09:51 | are interested only on one of them so the question is how to pick one of those |
| 2:09:56 | usually we search for a timestamp or date value to help us so if you check |
| 2:10:00 | the creation date over here we can understand that this record this one |
| 2:10:04 | over here is the newest one and the previous two are older than it so that |
| 2:10:09 | means if I have to go and pick one of those values I would like to get the |
| 2:10:13 | latest one because it holds the most fresh information so what we have to do |
| 2:10:18 | is we have to go and rank all those values based on the create dates and |
| 2:10:23 | only pick the highest one so that means we need a ranking function and for that |
| 2:10:28 | in scale we have the amazing window functions so let's go and do that we |
| 2:10:32 | will use the function row number over and then Partition by and here we have |
| 2:10:40 | to divide the table by the customer ID so we're going to divide it by the |
| 2:10:44 | customer ID and in order now to rank those rows we have to sort the data by |
| 2:10:49 | something so order by and as we discussed we want to sort the data by |
| 2:10:53 | the creation date so create date and we're going to sort it |
| 2:10:58 | descending so the highest first then the lowest so let's go and do that and now |
| 2:11:02 | we're going to go and give it the name flag last so now let's go and executed |
| 2:11:07 | now the data is sorted by the creation date and you can see over here that this |
| 2:11:12 | record is the number one then the one that is older is two and the oldest one |
| 2:11:16 | is three of course we are interested in the rank number one now let's go and |
| 2:11:21 | moove the filter and check everything so now if you have a look to the table you |
| 2:11:24 | can see that on the flag we have everywhere like one and that's because |
| 2:11:29 | the those primary Keys exist only one but sometimes we will not have one we |
| 2:11:33 | will have two three and so on if there's like duplicates we can go of course and |
| 2:11:37 | do a double check so let's go over here and say select |
| 2:11:40 | star from this query we're going to say where flag last is in equal to one so |
| 2:11:47 | let's go and query it and now we can see all the data that we don't need because |
| 2:11:51 | they are causing duplicates in the primary key and they have like an old |
| 2:11:54 | status so what we're going to do we're going to say equal to one and with that |
| 2:11:58 | we guarantee that our primary key is unique and each value exist only once so |
| 2:12:03 | if I go and query it like this you will see we will not find any duplicate |
| 2:12:07 | inside our table and we can go and check that of course so let's go and check |
| 2:12:11 | this primary key and we're going to say and customer ID equal to this value and |
| 2:12:16 | you can see it exists now only once and we are getting the freshest data from |
| 2:12:20 | this key so with that we have defined like transformation in order to remove |
| 2:12:25 | any D Kates okay so now moving on to the next one as you can see in our table we |
| 2:12:30 | have a lot of values where they are like string values now for these string |
| 2:12:35 | values we have to check the unwanted spaces so now let's go and write a query |
| 2:12:39 | that's going to detect those unwanted spaces so we're going to say |
| 2:12:43 | select this column the first name from our table bronze customer information so |
| 2:12:50 | let's go and query it now by just looking to the data it's going to be |
| 2:12:54 | really hard to find those unwanted spaces especially if they are at the end |
| 2:12:58 | of the world but there is a very easy way in order to detect those issues so |
| 2:13:03 | what we're going to do we're going to do a filter so now we're going to say the |
| 2:13:05 | first name is not equal to the first name after trimming the values so if you |
| 2:13:11 | use the function trim what it going to do it's going to go and remove all the |
| 2:13:15 | leading and trailing spaces so the first name so if this value is not equal to |
| 2:13:22 | the first name after trimming it then we have an issue so it is very simple let's |
| 2:13:26 | go and execute it so now in the result we will get the list of all first names |
| 2:13:31 | where we have spaces either at the start or at the end so again the expectation |
| 2:13:36 | here is no results and the same thing we can go and check something else like for |
| 2:13:42 | example the last name so let's go and do that over here and here let's go and |
| 2:13:48 | execute it we see in the result we have as well customers where they have like |
| 2:13:53 | space in their last name which is not really good and we can go and keep |
| 2:13:57 | checking all the string values that you have inside the table so for example the |
| 2:14:01 | gender so let's go and check that and execute now as you can see we |
| 2:14:07 | don't have any results that means the quality of the gender is better and we |
| 2:14:11 | don't have any unwanted spaces so now we have to go and write transformation in |
| 2:14:16 | order to clean up those two columns now what I'm going to do I'm just going to |
| 2:14:19 | go and list all the column in the query instead of the star all right so now I |
| 2:14:24 | have a list of all the columns that I need and now what we have to do is to go |
| 2:14:27 | to those two columns and start removing The Unwanted spaces so we'll just use |
| 2:14:32 | the trim it's very simple and give it a name of course the |
| 2:14:37 | same name and we will trim as well the last name so let's go and query this and |
| 2:14:43 | with that we have cleaned up those two colums from any unwanted spaces okay so |
| 2:14:47 | now moving on we have those two informations we have the marital status |
| 2:14:51 | and as well the gender if you check the values inside those two columns as you |
| 2:14:55 | can see we have here low cardinality so we have limited numbers of possible |
| 2:14:59 | values that is used inside those two columns so what we usually do is to go |
| 2:15:04 | and check the data consistency inside those two columns so it's very simple |
| 2:15:09 | what we're going to do we're going to do the following we're going to say |
| 2:15:13 | distinct and we're going to check the values let's go and do that and now as |
| 2:15:17 | you can see we have only three possible values either null F or M which is okay |
| 2:15:22 | we can stay like this of course but we can make a rule in our project where we |
| 2:15:26 | can say we will not be working with data abbreviations we will go and use only |
| 2:15:31 | friendly full names so instead of having an F we're going to have like a full |
| 2:15:36 | word female and instead of M we're going to have like male and we make it as a |
| 2:15:40 | rule for the whole project so each time we find the gender informations we try |
| 2:15:44 | to give the full name of it so let's go and map those two values to a friendly |
| 2:15:49 | one so we're going to go to the gender of over here and say case when and we're |
| 2:15:53 | going to say the gender is equal to F then make it a |
| 2:15:59 | female and when it is equal to |
| 2:16:05 | M then M it to male and now we have to make decision about the nulls as you can |
| 2:16:11 | see over here we have nulls so do we want to leave it as a null or we want to |
| 2:16:15 | use always the value unknown so with that we are replacing the missing values |
| 2:16:21 | with a standard default value or you can leave it as a null but let's say in our |
| 2:16:25 | project that we are replacing all the missing value with a default value so |
| 2:16:29 | let's go and do that we going to say else I'm going to go with the na not |
| 2:16:35 | available or you can go with the unknown of course so that's for the gender |
| 2:16:39 | information like this and we can go and remove the old one and now there is one |
| 2:16:43 | thing that I usually do in this case where sometimes what happens currently |
| 2:16:47 | we are getting the capital F and the capital M but maybe in the the time |
| 2:16:51 | something changed and you will get like lower M and lower F so just to make sure |
| 2:16:55 | in those cases we still are able to map those values to the correct value what |
| 2:17:00 | we're going to do we're going to just use the function upper just to make sure |
| 2:17:04 | that if we get any lowercase values we are able to catch it so the same thing |
| 2:17:10 | over here as well and now one more thing that you can add as well of course if |
| 2:17:15 | you are not trusting the data because we saw some unwanted spaces in the first |
| 2:17:19 | name and the last name you might not trust that in the future you will get |
| 2:17:22 | here as well unwanted spaces you can go and make sure to trim |
| 2:17:27 | everything just to make sure that you are catching all those cases so that's |
| 2:17:33 | it for now let's go and excute now as you can see we don't have an m and an F |
| 2:17:37 | we have a full word male and female and if we don't have a value we don't have a |
| 2:17:42 | null we are getting here not available now we can go and do the same stuff for |
| 2:17:47 | the Merial status you can see as well we have only three possibil ities the S |
| 2:17:51 | null and an M we can go and do the same stuff so I will just go and copy |
| 2:17:56 | everything from here and I will go and use the marital status I just remove |
| 2:18:01 | this one from here and now what are the possible values we have the S so it's |
| 2:18:05 | going to be single we have an M for married and we have as well a null and |
| 2:18:12 | with that we are getting the not available so with that we are making as |
| 2:18:15 | well data standardizations for this column so let's go and execute it now as |
| 2:18:21 | you can see we don't have those short values we have a full friendly value for |
| 2:18:25 | the status and as well for the gender and at the same time we are handling the |
| 2:18:29 | nulls inside those two columns so with that we are done with those two columns |
| 2:18:33 | and now we can go to the last one that create date for this type of |
| 2:18:36 | informations we make sure that this column is a real date and not as a |
| 2:18:41 | string or barar and as we defined it in the data type it is a date which is |
| 2:18:45 | completely correct so nothing to do with this column and now the next step is |
| 2:18:50 | that we're going to go and write the insert statement so how we're going to |
| 2:18:53 | do it we're going to go to the start over here and say insert into silver do |
| 2:18:59 | SRM customer info now we have to go and specify all the columns that should be |
| 2:19:04 | inserted so we're going to go and type it so something like this and then we |
| 2:19:08 | have the query over here let's go and execute it so let's do that so with that |
| 2:19:13 | we have inserted clean data inside the silver table so now what we're going to |
| 2:19:17 | do we're going to go and take all the queries that we have used used in order |
| 2:19:21 | to check the quality of the bronze and let's go and take it to another query |
| 2:19:25 | and instead of having bronze we're going to say silver so this is about the |
| 2:19:29 | primary key let's go and execute it perfect we don't have any results so we |
| 2:19:34 | don't have any duplicates the same thing for the next one so the silver and it |
| 2:19:40 | was for the first name so let's go and check the first name and run it as you |
| 2:19:46 | can see there is no results it is perfect we don't have any issues you can |
| 2:19:50 | of course go and check the last name and run it again we don't have any |
| 2:19:56 | result over here and now we can go and check those low cardinality columns like |
| 2:20:01 | for example the gender let's go and execute |
| 2:20:05 | it so as you can see we have the not available or the unknown male and female |
| 2:20:09 | so perfect and you can go and have a final look to the table to the silver |
| 2:20:14 | customer info let's go and check that so now we can have a look to all those |
| 2:20:18 | columns as you can see everything looks perfect and you can see it is working |
| 2:20:22 | this metadata information that we have added to the table definition now it |
| 2:20:26 | says when we have inserted all those three cords to the table which is really |
| 2:20:31 | amazing information to have a track and audit okay so now by looking to the |
| 2:20:35 | script we have done different types of data Transformations the first one is |
| 2:20:39 | with the first name and the last name here we have done trimming removing |
| 2:20:43 | unwanted spaces this is one of the types of data cleansing so we remove |
| 2:20:47 | unnecessary spaces or unwanted characters to to ensure data consistency |
| 2:20:52 | now moving on to the next transformation we have this casewin so what we have |
| 2:20:56 | done here is data normalization or we call it sometimes data standardization |
| 2:21:01 | so this transformation is type of data cleansing where we can map coded values |
| 2:21:06 | to meaningful userfriendly description and we have done the same transformation |
| 2:21:10 | as well to the agender another type of transformation that we have done as well |
| 2:21:15 | in the same case when is that we have handled the missing values so instead of |
| 2:21:19 | nulls we can have not available so handling missing data is as well type of |
| 2:21:24 | data cleansing where we are filling the blanks by adding for example a default |
| 2:21:29 | value so instead of having an empty string or a null we're going to have a |
| 2:21:33 | default value like the not available or unknown another type of data and |
| 2:21:36 | Transformations that we have done in this script is we have removed the |
| 2:21:40 | duplicates so removing duplicates is as well type of data cleansing where we |
| 2:21:44 | ensure only one record for each primary key by identifying and retaining only |
| 2:21:50 | the most relevant role to ensure there is no duplicates inside our data and as |
| 2:21:55 | we are removing the duplicates of course we are doing data filtering so those are |
| 2:21:59 | the different types of data Transformations that we have done in |
| 2:22:03 | this |
| 2:22:06 | script all right moving on to the second table in the bronze layer from the CRM |
| 2:22:11 | we have the product info and of course as usual before we start writing any |
| 2:22:15 | Transformations we have to search for data quality issues and we start with |
| 2:22:19 | the first one we have to check the primary key so we have to check whether |
| 2:22:22 | we have duplicates or nulls inside this key so what you have to do we have to |
| 2:22:26 | group up the data by the primary key or check whether we have nulls so let's go |
| 2:22:30 | and execute it so as you can see everything is safe we don't have dcat or |
| 2:22:34 | nulls in the primary key now moving on to the next one we have the product key |
| 2:22:38 | here we have in this column a lot of informations so now what you have to do |
| 2:22:41 | is to go and split this string into two informations so we are deriving new two |
| 2:22:46 | columns so now let's start with the first one is the category ID the first |
| 2:22:51 | five characters they are actually the category ID and we can go and use the |
| 2:22:55 | substring function in order to extract part of a string it needs three |
| 2:23:00 | arguments the first one going to be the column that we want to extract from and |
| 2:23:04 | then we have to define the position where to extract and since the first |
| 2:23:08 | part is on the left side we going to start from the first position and then |
| 2:23:12 | we have to specify the length so how many characters we want to extract we |
| 2:23:16 | need five characters so 1 2 3 4 five so that's set for the category ID category |
| 2:23:22 | ID let's go and execute it now as you can see we have a new column called the |
| 2:23:27 | category ID and it contains the first part of the string and in our database |
| 2:23:32 | from the other source system we have as well the category ID now we can go and |
| 2:23:36 | double check just in order to make sure that we can join data together so we're |
| 2:23:40 | going to go and check the ID from the pron table Erp and this can be from the |
| 2:23:47 | category so in this table we have the category ID and you can see over here |
| 2:23:52 | those are the IDS of the category and in the C layer we have to go and join those |
| 2:23:57 | two tables but here we still have an issue we have here an underscore between |
| 2:24:01 | the category and the subcategory but in our table we have actually a minus so we |
| 2:24:07 | have to replace that with an underscore in order to have matching informations |
| 2:24:11 | between those two tables otherwise we will not be able to join the tables so |
| 2:24:14 | we're going to use the function replace and what we are replacing we are |
| 2:24:19 | replacing the m with an underscore something like this |
| 2:24:24 | and if you go now and execute it we will get an underscore exactly like the other |
| 2:24:29 | table and of course we can go and check whether everything is matching by having |
| 2:24:33 | very simple query where we say this new information not in and then we have this |
| 2:24:40 | nice subquery so we are trying to find any category ID that is not available in |
| 2:24:46 | the second table so let's go and execute it now as you can see we have only one |
| 2:24:49 | category that is not matching we are not finding it in this table which is maybe |
| 2:24:54 | correct so if you go over here you will not find this category I just make it a |
| 2:24:59 | little bit bigger so we are not finding this one category from this table which |
| 2:25:03 | is fine so our check is okay okay so with that we have the first part now we |
| 2:25:07 | have to go and extract the second part and we're going to do the same thing so |
| 2:25:11 | we're going to use the substring and the three argument the product key but this |
| 2:25:15 | time we will not start cutting from the first position we have to be in the |
| 2:25:19 | middle so 1 2 2 3 4 5 6 7 so we start from the position number seven and now |
| 2:25:26 | we have to define the length how many characters to be extracted but if you |
| 2:25:30 | look over here you can see that we have different length of the product keys it |
| 2:25:35 | is not fixed like the category ID so we cannot go and use specified number we |
| 2:25:39 | have to make something Dynamic and there is Trick In order to do that we can to |
| 2:25:43 | go and use the length of the whole column with that we make sure that we |
| 2:25:47 | are always getting enough characters to be extra Ed and we will not be losing |
| 2:25:51 | any informations so we will make it Dynamic like this we will not have it as |
| 2:25:56 | a fixed length and with that we have the product key so let's go and execute it |
| 2:26:02 | as you can see we are now extracting the second part from this string now why we |
| 2:26:07 | need the product key we need it in order to join it with another table called |
| 2:26:12 | sales details so let's go and check the sales details so let me just check the |
| 2:26:17 | column name it is SLS product key so from bronze |
| 2:26:24 | CRM sales let's go and check the data over here and it looks wonderful so |
| 2:26:31 | actually we can go and join those informations together but of course we |
| 2:26:34 | can go and check that so we're going to say where and we're going to take our |
| 2:26:37 | new column and we're going to say not in the subquery just to make sure that we |
| 2:26:42 | are not missing anything so let's go and execute so it looks like we have a lot |
| 2:26:47 | of products that don't have any orders well I don't have a nice feelings about |
| 2:26:53 | it let's go and try something like this one here and we say where LS BRD key |
| 2:27:00 | like this value over here so I'll just cut the last three just to search inside |
| 2:27:06 | this table so we really don't have such a keys let me just cut the second one so |
| 2:27:12 | let's go and search for it we don't have it as well so anything that starts with |
| 2:27:17 | the FK we don't have any order with the product where it starts with the F key |
| 2:27:22 | so let's go and remove it but still we are able to join the tables right so if |
| 2:27:27 | I go and say in instead of not in so with that you are able to match all |
| 2:27:32 | those products so that means everything is fine actually it's just products that |
| 2:27:37 | don't have any orders so with that I'm happy with this transformation now |
| 2:27:42 | moving on to the next one we have here the name of the product we can go and |
| 2:27:46 | check whether there is unwanted spaces so let's go to our quality checks make |
| 2:27:51 | sure to use the same table and we're going to use the product name and check |
| 2:27:56 | whether we find any unmatching after trimming so let's go and do it well it |
| 2:28:01 | looks really fine so we don't have to trim anything this column is safe now |
| 2:28:06 | moving on to the next one we have the costs so here we have numbers and we |
| 2:28:10 | have to check the quality of the numbers so what we can do we can check whether |
| 2:28:14 | we have nulls or negative numbers so negative costs or negative prices which |
| 2:28:19 | is not really realistic depend on the business of course so let's say in our |
| 2:28:22 | business we don't have any negative costs so it's going to be like this |
| 2:28:27 | let's go and check whether is something less than zero or whether we have costs |
| 2:28:33 | that is null so let's go and check those informations well as you can see we |
| 2:28:39 | don't have any negative values but we have nulls so we can go and handle that |
| 2:28:43 | by replacing the null with a zero of course if the business allow that so in |
| 2:28:48 | SQL server in order to replace the null with a zero we have a very nice function |
| 2:28:52 | called is null so we are saying if it is null then replace this value with a zero |
| 2:28:59 | it is very simple like this and we give it a name of course so let's go and |
| 2:29:04 | execute it and as you can see we don't have any more nulls we have zero which |
| 2:29:09 | is better for the calculations if you are later doing any aggregate functions |
| 2:29:13 | like the average now moving on to the next one we have the product line This |
| 2:29:17 | is again abbreviation of something and the cardinality is low so let's go and |
| 2:29:21 | check all possible values inside this column so we're just going to use the |
| 2:29:26 | distinct going to be BRD line so let's go and execute it and as you can see the |
| 2:29:31 | possible values are null Mr rst and again those are abbreviations but in our |
| 2:29:36 | data warehouse we have decided to give full nice names so we have to go and |
| 2:29:41 | replace those codes those abbreviations with a friendly value and of course in |
| 2:29:46 | order to get those informations I usually go and ask the expert from the |
| 2:29:50 | The Source system or an expert from the process so let's start building our case |
| 2:29:55 | win and then let's use the upper and as well the trim just to make sure that we |
| 2:30:00 | are having all the cases so the BRD line is equal to so let's start with the |
| 2:30:07 | first value the M then we will get the friendly value it's going to be Mountain |
| 2:30:14 | then to the next one so I will just copy and paste here if it is an R then it is |
| 2:30:20 | rods and another one for let me check what do we have here we have Mr and then |
| 2:30:27 | s the S stands for other sales and we have the T so let's go and get the T so |
| 2:30:35 | the T stands for touring we have at the end an else for |
| 2:30:40 | unknown not available so we don't need any nulls so that's it and we're going |
| 2:30:45 | to name it as before so product line so let's remove the old one and let's |
| 2:30:50 | execute it and as you can see we don't have here anymore those shortcuts and |
| 2:30:55 | the abbreviations we have now full friendly value but I will go and have |
| 2:31:00 | here like capital O it looks nicer so that we have nice friendly value now by |
| 2:31:05 | looking to this case when as you can see it is always like we are mapping one |
| 2:31:08 | value to another value and we are repeating all time upper time upper time |
| 2:31:13 | and so on we have here a quick form in the case when if it is just a simple |
| 2:31:17 | mapping so the syntax is very simple we say case and then we have the column so |
| 2:31:23 | we are evaluating this value over here and then we just say when without the |
| 2:31:28 | equal so if it is an M then make it Mountain the same thing for the next one |
| 2:31:33 | and so so with that we have the functions only once and we don't have to |
| 2:31:38 | go and keep repeating the same function over and over and this one only if you |
| 2:31:41 | are mapping values but if you have complex conditions you can do it like |
| 2:31:45 | this but for now I'm going to stay with the quick form of the case wi it looks |
| 2:31:49 | nicer and shorter so let's go and execute it we will get the same results |
| 2:31:53 | okay so now back to our table let's go to the last two columns we have the |
| 2:31:56 | start and end date so it's like defining an interval we have start and end so |
| 2:32:01 | let's go and check the quality of the start and end dates we're going to go |
| 2:32:04 | and say select star from our bronze table and now we're |
| 2:32:09 | going to go and search it like this we are searching for the end date that is |
| 2:32:14 | smaller than the starts so PRT start dates so let's let's go and query this |
| 2:32:21 | so you can see the start is always like after the end which makes no sense at |
| 2:32:26 | all so we have here data issue with those two dates so now for this kind of |
| 2:32:29 | data Transformations what I usually do is I go and grab few examples and put it |
| 2:32:34 | in Excel and try to think about how I'm going to go and fix it so here I took |
| 2:32:38 | like two products this one and this one over here and for that we have like |
| 2:32:41 | three rows for each one of them and we have this situation over here so the |
| 2:32:45 | question now how we going to go and fix it I will go and make like a copy of one |
| 2:32:49 | solution where we're going to say it's very simple let's go and switch the |
| 2:32:53 | start date with the end date so if I go and grab the end dates and put it at the |
| 2:32:58 | starts things going to look way nicer right so we have the start is always |
| 2:33:02 | younger than the end but my friends the data now makes no sense because we say |
| 2:33:07 | it starts from 2007 and ends by 2011 the price was 12 but between 2018 and 2012 |
| 2:33:15 | we have 14 which is not really good because if you take for example the year |
| 2:33:20 | 2010 for 2010 it was 12 and at the same time 14 so it is really bad to have an |
| 2:33:26 | overlapping between those two dates it should start from 2007 and end with 11 |
| 2:33:32 | and then start febe from 12 and end with something else there should be no |
| 2:33:36 | overlapping between years so it's not enough to say the start should be always |
| 2:33:41 | smaller than the end but as well the end of the first history should be younger |
| 2:33:47 | than the start of the next records this is as well a rule in order to have no |
| 2:33:52 | overlapping this one has no start but has already an end which is not really |
| 2:33:57 | okay because we have always to have a starts each new record in historization |
| 2:34:02 | has to has a start so for this record over here this is as well wrong and of |
| 2:34:07 | course it is okay to have the start without an end so in this scenario it's |
| 2:34:11 | fine because this indicate this is the current informations about the costs so |
| 2:34:16 | again this solution is not working at all so now for for the solution to what |
| 2:34:20 | we can say let's go and ignore completely the end date and we take only |
| 2:34:25 | the start dates so let's go and paste it over here but now we go and rebuild the |
| 2:34:29 | end date completely from the start date following the rules that we have defined |
| 2:34:34 | so the rule says the end of date of the current records comes from the start |
| 2:34:39 | date from the next records so here this end date comes from this value over here |
| 2:34:45 | from the next record so that means we take the next start date and put it at |
| 2:34:49 | the end date for the previous records so with that as you can see it is working |
| 2:34:53 | the end date is higher than the start dates and as well we are making sure |
| 2:34:58 | this date is not overlapping with the next record but as well in order to make |
| 2:35:02 | it way nicer we can subtract it with one so we can take the previous day like |
| 2:35:08 | this so with that we are making sure the end date is smaller than the next start |
| 2:35:13 | now for the next record this one over here the end date going to come from the |
| 2:35:18 | next start date so we will take this one for here and put it as an end Ag and |
| 2:35:22 | subtract it with one so we will get the previous day so now if you compare those |
| 2:35:28 | two you can see it's still higher than the start and if you compare it with the |
| 2:35:32 | NY record this one over here it is still smaller than the next one so there is no |
| 2:35:37 | overlapping and now for the last record since we don't have here any |
| 2:35:40 | informations it will be a null which is totally fine so as you can see I'm |
| 2:35:45 | really happy with this scenario over here of course you can go and validate |
| 2:35:48 | this with an exp from The Source system let's say I've done that and they |
| 2:35:52 | approved it and now I can go and clean up the data using this New Logic so this |
| 2:35:57 | is how I usually brainstorm about fixing an issues if I have like a complex stuff |
| 2:36:01 | I go and use Excel and then discuss it with the expert using this example it's |
| 2:36:05 | way better than showing a database queries and so on it just makees things |
| 2:36:10 | easier to explain and as well to discuss so now how I usually do it I usually go |
| 2:36:14 | and make a focus on only the columns that I need and take only one two |
| 2:36:18 | scenarios while I'm building the logic and once everything is ready I go and |
| 2:36:22 | integrate it in the query so now I'm focusing only on these columns and only |
| 2:36:26 | for these products so now let's go and build our logic now in SQL if you are at |
| 2:36:31 | specific record and you want to access another information from another records |
| 2:36:36 | and for that we have two amazing window functions we have the lead and lag in |
| 2:36:40 | this scenario we want to access the next records that's why we have to go with |
| 2:36:44 | the function lead so let's go and build it lead and then what do we need we need |
| 2:36:48 | the lead or the |
| 2:36:50 | start date so we want the start date of the next records and then we say over |
| 2:36:56 | and we have to partition the data so the window going to be focusing on only one |
| 2:37:02 | product which is the product key and not the product ID so we are dividing the |
| 2:37:06 | data by product key and of course we have to go and sort the data so order by |
| 2:37:10 | and we are sorting the data by the start dates and ascending so from the lowest |
| 2:37:16 | to the highest and let's go and give it another name so as let's say test for |
| 2:37:21 | example just to test the data so let's go and execute and I think I missed |
| 2:37:26 | something here it say Partition by so let's go and execute again and now let's |
| 2:37:30 | go and check the results for the first partition over here so the start is 2011 |
| 2:37:35 | and the end is 2012 and this information came from the next record so this data |
| 2:37:41 | is moved to the previous record over here and the same thing for this record |
| 2:37:45 | so the end date comes from the next record so our logic is working and the |
| 2:37:50 | last record over here is null because we are at the end of the window and there |
| 2:37:54 | is no next data that's why we will get null and this is perfect of course so it |
| 2:37:58 | looks really awesome but what is missing is we have to go and get the previous |
| 2:38:03 | day and we can do that very simply using minus one we are just subtracting one |
| 2:38:07 | day so we have no overlapping between those two dates and the same thing for |
| 2:38:11 | those two dates so as you can see we have just buil a perfect end date which |
| 2:38:15 | is way better than the original data that we got from the source system now |
| 2:38:19 | let's take this one over here and put it inside our query so we don't need the |
| 2:38:24 | end H we need our new end dat we just remove that test and execute now it |
| 2:38:30 | looks perfect all right now we are not done yet with those two dates actually |
| 2:38:35 | we are saying all time dates because we don't have here any informations about |
| 2:38:39 | the time always zero so it makes no sense to have these informations inside |
| 2:38:44 | our data so what we can do we can do a very simple cast and we make this column |
| 2:38:49 | as a date instead of date time so this is for the first one and as well for the |
| 2:38:54 | next one as dates so let's try that out and as you can see it is nicer we don't |
| 2:38:59 | have the time informations of course we can tell the source systems about all |
| 2:39:03 | those issues but since they don't provide the time it makes no sense to |
| 2:39:07 | have date and time okay so it was a long run but we have now cleaned product |
| 2:39:12 | informations and this is way nicer than the original product information that we |
| 2:39:16 | got from the source CRM so if you grab the ddl of the server table you can see |
| 2:39:20 | that we don't have a category ID so we have product ID and product key and as |
| 2:39:25 | well those two columns we just change the data type so it's date time here but |
| 2:39:29 | we have changed that to a date so that means we have to go and do few |
| 2:39:33 | modifications to the ddl so what we going to do we're going to go over here |
| 2:39:36 | and say category ID and I will be using the same data type and for the start and |
| 2:39:41 | end this time it's going to be date and not date and time so that's it for now |
| 2:39:45 | let's go ah and execute it in order to repair the ddl and this is what happen |
| 2:39:49 | in the silver layer sometimes we have to adjust the metadata if the quality of |
| 2:39:54 | the data types and so on is not good or we are building new derived informations |
| 2:39:58 | in order later to integrate the data so it will be like very close to the bronze |
| 2:40:02 | layer but with few modifications so make sure to update your ddl scripts and now |
| 2:40:08 | the next step is that we're going to go and insert the data into the table and |
| 2:40:12 | now the next step we're going to go and insert the result of this query that is |
| 2:40:16 | cleaning up the bronze table into the silver table so as we' done it before |
| 2:40:20 | insert into silver the product info and then we have to go and list all the |
| 2:40:25 | columns I've just prepared those columns so with that we can go and now run our |
| 2:40:31 | query in order to insert the data so now as you can see SQL did insert the data |
| 2:40:35 | and the very important step is now to check the quality of the silver table so |
| 2:40:39 | we go back to our data quality checks and we go switch to the silver so let's |
| 2:40:44 | check the primary key there is no issues and we can go and check for example here |
| 2:40:49 | the the trims there is as well no issue and now let's go and check the costs it |
| 2:40:54 | should not be negative or null which is perfect let's go and check the data |
| 2:40:59 | standardizations as you can see they are friendly and we don't have any nulls and |
| 2:41:03 | now very interesting the order of the dates so let's go and check that as you |
| 2:41:07 | can see we don't have any issues and finally what I do I go and have a final |
| 2:41:13 | look to the silver table and as we can see everything is inserted correctly in |
| 2:41:18 | the correct color colums so all those columns comes from the source system and |
| 2:41:22 | the last one is automatically generated from the ddl indicate when we loaded |
| 2:41:27 | this table now let's sit back and have a look to our script what are the |
| 2:41:30 | different types of data Transformations that we have done here is for example |
| 2:41:34 | over here the category ID and the product key we have derived new columns |
| 2:41:38 | so it is when we create a new column based on calculations or transformations |
| 2:41:43 | of an existing one so sometimes we need columns only for analytics and we cannot |
| 2:41:48 | each time go to the source system and ask them to create it so instead of that |
| 2:41:52 | we derive our own columns that we need for the analytics another transformation |
| 2:41:56 | we have is that is null over here so we are handling here missing information |
| 2:42:01 | instead of null we're going to have a zero and one more transformation we have |
| 2:42:05 | over here for the product line we have done here data normalization instead of |
| 2:42:09 | having a code value we have a friendly value and as well we have handled the |
| 2:42:14 | missing data for example over here instead of having a null we're going to |
| 2:42:17 | have not available all right moving on to another data transformation we have |
| 2:42:21 | done data type casting so we are converting the data type from one to |
| 2:42:25 | another and this considered as well to be a data transformation and now moving |
| 2:42:29 | on to the last one we are doing as well data type casting but what's more |
| 2:42:33 | important we are doing data enrichment this type of transformation it's all |
| 2:42:37 | about adding a value to your data so we are adding a new relevant data to our |
| 2:42:42 | data sets so those are the different types of data Transformations that we |
| 2:42:47 | have done for this table |
| 2:42:52 | okay so let's keep going we have the sales details and this is the last table |
| 2:42:55 | in the CRM so what do you have over here we have the order number and this is a |
| 2:42:59 | string of course we can go and check whether we have an issue with the |
| 2:43:02 | unwanted spaces so we can search whether we're going to find something so we can |
| 2:43:06 | say trim and something like this and let's go and execute it so we can see |
| 2:43:10 | that we don't have any unwanted spaces that means we don't have to transform |
| 2:43:14 | this column so we can leave it as it is now the next two columns they are like |
| 2:43:18 | keys and ideas is in order to connect it with the other tables as we learned |
| 2:43:22 | before we are using the product key in order to connect it with the product |
| 2:43:26 | informations and we are connecting the customer ID with the customer ID from |
| 2:43:30 | the customer info so that means we have to go and check whether everything is |
| 2:43:33 | working perfectly so we can go and check the Integrity of those columns where we |
| 2:43:37 | say the product key Nots in and then we make a subquery and this time we can |
| 2:43:42 | work with the silver layer right so we can say the product key from Silver do |
| 2:43:48 | product info so let's go and query this and as you can see we are not getting |
| 2:43:52 | any issue that means all the product keys from the sales details can be used |
| 2:43:56 | and connected with the product info the same thing we can go and check the |
| 2:44:00 | Integrity of the customer ID and we can use not the products we can go to the |
| 2:44:04 | customer info and the name was CST ID so let's go and query that and the same |
| 2:44:10 | thing we don't have here any issues so that means we can go and connect the |
| 2:44:13 | sales with the customers using the customer ID and we don't have to do any |
| 2:44:17 | Transformations for it so things looks really nice for those three columns now |
| 2:44:21 | we come to the challenging one we have here the dates now those dates are not |
| 2:44:26 | actual dates they are integer so those are numbers and we don't want to have it |
| 2:44:30 | like this we would like to clean that up we have to change the data type from |
| 2:44:34 | integer to a DAT now if you want to convert an integer to a date we have to |
| 2:44:38 | be careful with the values that we have inside each of those columns so now |
| 2:44:42 | let's check the quality for example of the order dates let's say where order |
| 2:44:46 | dates is less than zero for example something negative well we don't have |
| 2:44:51 | any negative values which is good let's go and check whether we have any zeros |
| 2:44:55 | well this is bad so we have here a lot of zeros now what we can do we can |
| 2:44:59 | replace those informations with a null we can use of course the null IF |
| 2:45:03 | function like this we can say null if and if it is zero then make it null so |
| 2:45:08 | let's execute it and as you can see now all those informations are null now |
| 2:45:13 | let's go and check again the data so now this integer has the years information |
| 2:45:17 | at the start then the months and then the day so here we have to have like 1 2 |
| 2:45:21 | 3 4 5 so the length of each number should be H and if the length is less |
| 2:45:26 | than eight or higher than eight then we have an issue let's go and check that so |
| 2:45:30 | we're going to say or length sales order is not equal to eight that means less or |
| 2:45:37 | higher let's go and execute it now let's go and check the results over here and |
| 2:45:41 | those two informations they don't look like dates so we cannot go and make from |
| 2:45:45 | these informations a real dates they are just bad data and of course you can go |
| 2:45:50 | and check the boundaries of a DAT like for example it should not be higher than |
| 2:45:55 | for example let's go and get this value 2050 and then I need for the month and |
| 2:45:59 | the date so let's go and execute it and if we just remove those informations |
| 2:46:03 | just to make sure so we don't have any date that is outside of the boundaries |
| 2:46:07 | that you have in your business or you go for example and say the boundary should |
| 2:46:11 | be not less than depend when your business started maybe something like |
| 2:46:15 | this we are getting of course those values because they are less than n but |
| 2:46:19 | if you have values around these dates you will get it as well in the query so |
| 2:46:23 | we can go and add the rests so all those checks like validate the column that has |
| 2:46:28 | date informations and it has the data type integer so again what are the |
| 2:46:32 | issues over here we have zeros and sometimes we have like strange numbers |
| 2:46:37 | that cannot be converted to a dates so let's go and fix that in our query so we |
| 2:46:41 | can say case when the sales order the order date is equal to zero or of the |
| 2:46:47 | order date is not equal to 8 then null right we don't want to deal with those |
| 2:46:52 | values they are just wrong and they are not real dates otherwise we say else |
| 2:46:57 | it's going to be the order dates now what we're going to do we're going to go |
| 2:47:00 | and convert this to a date we don't want this as an integer so how we can do that |
| 2:47:04 | we can go and cast it first to varar because we cannot cast from integer to |
| 2:47:10 | date in SQL Server first you have to convert it to a varar and then from |
| 2:47:15 | varar you go to a dates well this is how we do it in scq server so we cast it |
| 2:47:19 | first to a varar and then we cast it to a date like this that's it so we have |
| 2:47:25 | end and we are using the same column name so this is how we transform an |
| 2:47:31 | integer to a date so let's go and query this and as you can see the order date |
| 2:47:36 | now is a real date it is not a number so we can go and get rid of the old column |
| 2:47:41 | now we have to go and do the same stuff for the shipping dates so we can go over |
| 2:47:45 | here and replace everything with the shipping date and let's go query well as |
| 2:47:50 | you can see the shipping date is perfect we don't have any issue with this column |
| 2:47:54 | but still I don't like that we found a lot of issues with the order dates so |
| 2:47:57 | what we're going to do just in case this happens for the shipping date in the |
| 2:48:00 | future I will go and apply the same rules to the shipping dates oh let's |
| 2:48:05 | take the shipping date like this and if you don't want to |
| 2:48:09 | apply it now you have always to build like quality checks that runs every day |
| 2:48:14 | in order to detect those issues and once you detect it then you can go and do the |
| 2:48:18 | Transformations but for now I'm going to apply it right away so that is for the |
| 2:48:22 | shipping date now we go to the due date and we will do the same |
| 2:48:26 | test let's go and execute it and as well it is perfect so still I'm going to |
| 2:48:32 | apply the same rules so let's get the D everywhere here in the query just make |
| 2:48:36 | sure you don't miss anything here so let's go and execute now perfect as you |
| 2:48:41 | can see we have the order date shipping date and due date and all of them are |
| 2:48:45 | date and don't have any wrong data inside those columns now still there is |
| 2:48:49 | one more check that we can do and is that the order date should be always |
| 2:48:53 | smaller than the shipping date or the due date because it's makes no sense |
| 2:48:57 | right if you are delivering an item without an order so first the order |
| 2:49:01 | should happen then we are shipping the items so there is like an order of those |
| 2:49:05 | dates and we can go and check that so we are checking now for invalid date orders |
| 2:49:09 | where we going to say the order date is higher than the shipping date or we are |
| 2:49:15 | searching as well for an order where the order date date is higher than the due |
| 2:49:20 | dates so we going to have it like this due dates so let's go and check well |
| 2:49:24 | that's really good we don't have such a mistake on the data and the quality |
| 2:49:28 | looks good so the order date is always smaller than the shipping date or the |
| 2:49:33 | due dates so we don't have to do any Transformations or cleanup okay friends |
| 2:49:37 | now moving on to the last three columns we have the sales quantity and the price |
| 2:49:41 | all those informations are connected to each others so we have a business rule |
| 2:49:45 | or calculation it says the sales must be equal to quantity multiplied by the |
| 2:49:50 | price and all sales quantity and price informations must be positive numbers so |
| 2:49:55 | it's not allowed to be negative zero or null so those are the business rules and |
| 2:50:00 | we have to check the data consistency in our table does all those three |
| 2:50:04 | informations following our rules so we're going to start first with our rule |
| 2:50:08 | right so we're going to say if the sales is not equal to quantity multiplied by |
| 2:50:15 | the price so we are searching where the result is not matching our expectation |
| 2:50:20 | and as well we can go and check other stuff like the nulls so for example we |
| 2:50:23 | can say or sales is null or quantity is null and the last one for the price and |
| 2:50:33 | as well we can go and check whether they are negative numbers or zero so we can |
| 2:50:38 | go over here and say less or equal to zero and apply it for the other columns |
| 2:50:42 | as well so with that we are checking the calculation and as well we are checking |
| 2:50:47 | whether we have null0 Z or negative numbers let's go and check our |
| 2:50:51 | informations I'm going to have here A distinct so let's go and query it and of |
| 2:50:56 | course we have here bad data but we can go and sort the data by the sales |
| 2:51:01 | quantity and the price so let's do it now by looking to the data we can see in |
| 2:51:06 | the sales we have nulls we have negative numbers and zeros so we have all bad |
| 2:51:12 | combinations and as well we have here bad calculations so as you can see the |
| 2:51:16 | price here is 50 the quantity is one but the sales is two which is not correct |
| 2:51:20 | and here we have as well wrong calculations here we have to have a 10 |
| 2:51:23 | and here nine or maybe the price is wrong and by looking to the quantity now |
| 2:51:28 | you can see we don't have any nulls we don't have any zeros or negative numbers |
| 2:51:32 | so the quantity looks better than the sales and if you look to the prices we |
| 2:51:36 | have nulls we have negatives and yeah we don't have zeros so that means the |
| 2:51:40 | quality of the sales and the price is wrong the calculation is not working and |
| 2:51:44 | we have these scenarios now of course how I do it here I don't go and try now |
| 2:51:48 | to transform everything on my own I usually go and talk to an expert maybe |
| 2:51:53 | someone from the business or from the source system and I show those scenarios |
| 2:51:56 | and discuss and usually there is like two answers either they going to tell me |
| 2:52:00 | you know what I will fix it in my source so I have to live with it there is |
| 2:52:04 | incoming bad data and the bad data can be presented in the warehouse until the |
| 2:52:08 | source system clean up those issues and the other answer you might get you know |
| 2:52:12 | what we don't have the budget and those data are really old and we are not going |
| 2:52:16 | to do anything so here you have to decide either you leave it as it is or |
| 2:52:20 | you say you know what let's go and improve the quality of the data but here |
| 2:52:23 | you have to ask for the experts to support you solving these issues because |
| 2:52:28 | it really depend on their rules different rules makes different |
| 2:52:31 | Transformations so now let's say that we have the following rules if the sales |
| 2:52:35 | informations are null or negative or zero then use the calculation the |
| 2:52:39 | formula by multiplying the quality with the price and now if the prices are |
| 2:52:44 | wrong for example we have here null or zero then go and calculate it from the |
| 2:52:48 | sales and a quantity and if you have a price that is a minus like minus 21 a |
| 2:52:54 | negative number then you have to go and convert it to a 21 so from a negative to |
| 2:52:59 | a positive without any calculations so those are the rules and now we're going |
| 2:53:02 | to go and build the Transformations based on those rules so let's do it step |
| 2:53:06 | by step I will go over here and we're going to start building the new sales so |
| 2:53:11 | what is the rule Sals case when of course as usual if the |
| 2:53:15 | sales is null or let's say the sales is negative number or equal to zero or |
| 2:53:22 | another scenario we have a sales information but it is not following the |
| 2:53:26 | calculation so we have wrong information in the sales so we're going to say the |
| 2:53:30 | sales is not equal to the quantity multiplied by the price but of course we |
| 2:53:36 | will not leave the price like this by using the function APS the absolute it's |
| 2:53:41 | going to go and convert everything from negative to a positive then what we have |
| 2:53:44 | to do is to go and use the calculation so so it's going to be the quantity |
| 2:53:50 | multiplied by the price so that means we are not using the value that come from |
| 2:53:54 | the source system we are recalculating it now let's say the sales is correct |
| 2:53:59 | and not one of those scenarios so we can say else we will go with the sales as it |
| 2:54:04 | is that comes from the source because it is correct it's really nice let's go and |
| 2:54:08 | say an end and give it the same name I will go and rename the old one here as |
| 2:54:13 | an old value and the same for the price the quantity will not T it because it is |
| 2:54:19 | correct so like this and now let's go and transform the prices so again as |
| 2:54:24 | usual we go with case wi so what are the scenarios the price is null or the price |
| 2:54:32 | is less or equal to zero then what we're going to do we're going to do the |
| 2:54:36 | calculation so it going to be the sales divided by the quantity the SLS quantity |
| 2:54:42 | but here we have to make sure that we are not dividing by zero currently we |
| 2:54:46 | don't have any zeros in the quantity but you don't know future you might get a |
| 2:54:49 | zero and the whole code going to break so what you have to do is to go and say |
| 2:54:53 | if you get any zero replace it with a null so null if if it is zero then make |
| 2:54:59 | it null so that's it now if the price is not null and the price is not negative |
| 2:55:04 | or equal to zero then everything is fine and that's why we're going to have now |
| 2:55:07 | the else it's going to be the price as it is from The Source system so that's |
| 2:55:13 | it we're going to say end as price so I'm totally happy with that let's go and |
| 2:55:17 | execute it and check of course so those are the old informations and those are |
| 2:55:21 | the new transformed cleaned up informations so here previously we have |
| 2:55:24 | a null but now we have two so two multiply with one we are getting two so |
| 2:55:29 | the sales is here correct now moving on to the next one we have in the sales 40 |
| 2:55:34 | but the price is two so two multiplied with one we should get two so the new |
| 2:55:39 | sales is correct it is two and not 40 now to the next one over here the old |
| 2:55:43 | sales is zero but if you go and multiply the four with the quantity you will get |
| 2:55:47 | four so the sales here is not correct that's why in the new sales we have it |
| 2:55:51 | correct as a four and let's go and get a minus so in this case we have a minus |
| 2:55:55 | which is not correct so we are getting the price multiplied with one we should |
| 2:55:59 | get here a nine and this sales here is correct now let's go and get a scenario |
| 2:56:04 | where the price is a null like this here so we don't have here price but we |
| 2:56:08 | calculated from the sales and the quantity so we divided the 10 by two and |
| 2:56:13 | we have five so the new price is better and the same thing for the minuses so we |
| 2:56:18 | have here minus 21 and in the output we have 21 which is correct so for now I |
| 2:56:22 | don't see any scenario where the data is wrong so everything looks better than |
| 2:56:27 | before and with that we have applied the business rules from the experts and we |
| 2:56:32 | have cleaned up the data in the data warehouse and this is way better than |
| 2:56:35 | before because we are presenting now better data for analyzes and Reporting |
| 2:56:40 | but it is challenging and you have exactly to understand the business so |
| 2:56:43 | now what we're going to do we're going to go and copy those informations and |
| 2:56:47 | integrate it in our query so instead of sales we're going to get our new |
| 2:56:51 | calculation and instead of the price we will get our correct calculation and |
| 2:56:56 | here I'm missing the end let's go and run the whole thing again so with that |
| 2:57:01 | we have as well now cleaned sales quantity and price and it is following |
| 2:57:06 | our business rules so with that we are done cleaning up the sales details The |
| 2:57:11 | Next Step we're going to go and inserted to the sales details but we have to go |
| 2:57:14 | and check again the ddl so now all what you have to do is to compare those |
| 2:57:18 | results with the ddl so the first one is the order number it's fine the product |
| 2:57:22 | key the customer ID but here we have an issue all those informations now are |
| 2:57:27 | date and not an integer so we have to go and change the data type and with that |
| 2:57:31 | we have better data type than before then the sales quantity price it is |
| 2:57:35 | correct let's go and drop the table and create it from scratch again and don't |
| 2:57:40 | forget to update your ddl script so that's it for this and we're going to go |
| 2:57:44 | now and insert the results into our silver table say details and we have to |
| 2:57:49 | go and list now all the columns I have already prepared the list of all the |
| 2:57:53 | columns so make sure that you have the correct order of the columns so let's go |
| 2:57:57 | now and insert the data and with that and with that we can see that the SQL |
| 2:58:02 | did insert data to our sales details but now very important is to check the |
| 2:58:06 | health of the silver table so what we going to do instead here of bronze we're |
| 2:58:10 | going to go and switch it to Silver so let's check over here so here always the |
| 2:58:14 | order is smaller than the shipping and the due date which is really nice but |
| 2:58:19 | now I'm very interested on the calculations so here we're going to |
| 2:58:23 | switch it from bronze to Silver and I'm going to go and get rid of all those |
| 2:58:26 | calculations because we don't need it this and now let's see whether we have |
| 2:58:31 | any issue well perfect our data is following the business rules we don't |
| 2:58:35 | have any nulls negative values zeros now as usual the last step the final check |
| 2:58:41 | we will just have a final look to the table so we have the order number the |
| 2:58:44 | product key the customer ID the three dates we have have the sales quantity |
| 2:58:49 | and the price and of course we have our metadata column everything is perfect so |
| 2:58:54 | now by looking to our code what are the different types of data Transformations |
| 2:58:58 | that we are doing so in those three columns we are doing the following so at |
| 2:59:02 | the start we are handling invalid data and this is as well type of |
| 2:59:06 | transformation and as well at the same time we are doing data type casting so |
| 2:59:11 | we are changing it to more correct data type and if you are looking to the sales |
| 2:59:15 | over here then what we are doing over here is we are handling the missing data |
| 2:59:19 | and as well the invalid data by deriving the column from already existing one and |
| 2:59:26 | it is as well very similar for the price we are handling as well the invalid data |
| 2:59:31 | by deriving it from specific calculation over here so those are the different |
| 2:59:35 | types of data Transformations that you have done in these |
| 2:59:41 | scripts all right now let's keep moving to the next our system we have the |
| 2:59:46 | customer AZ 12 so here we have we have like only three columns and let's start |
| 2:59:50 | with the ID first so here again we have the customers informations and if we go |
| 2:59:54 | and check again our model you can see that we can connect this table with the |
| 2:59:59 | CRM table customer info using the customer key so that means we have to go |
| 3:00:03 | and make sure that we can go and connect those two tables so let's go and check |
| 3:00:09 | the other table we can go and check of course the silver layer so let's query |
| 3:00:13 | it and we can query both of the tables now we can see there is here like exract |
| 3:00:18 | characters that are not included in the customer key from the CRM so let's go |
| 3:00:23 | and search for example for this customer over here where C ID like so we are |
| 3:00:31 | searching for customer has similar ID now as you can see we are finding this |
| 3:00:35 | customer but the issue is that we have those three characters in as there is no |
| 3:00:40 | specifications or explanation why we have the nas so actually what we have to |
| 3:00:44 | do is to go and remove those informations we don't need it so let's |
| 3:00:48 | again check the data so it looks like the old data have an Nas at the start |
| 3:00:53 | and then afterward we have new data without those three characters so we |
| 3:00:56 | have to clean up those IDs in order to be able to connect it with other tables |
| 3:01:01 | so we're going to do it like this we're going to start with the case wiin since |
| 3:01:04 | we have like two scenarios in our data so if the C ID is like the three |
| 3:01:10 | characters in as so if the ID start with those three characters then we're going |
| 3:01:15 | to go and apply transformation function otherwise eyes it's going to stay like |
| 3:01:19 | it is so that's it so now we have to go and build the transformation so we're |
| 3:01:25 | going to use substring and then we have to define the string it's going to be |
| 3:01:30 | the C ID and then we have to define the position where it start cutting or |
| 3:01:34 | extracting so we can say 1 2 3 and then four so we have to define the position |
| 3:01:40 | number four and then we have to define the string how many characters should be |
| 3:01:44 | extracted I will make it Dynamic so I will go with the link |
| 3:01:48 | I will not go and count how much so we're going to say the C ID so it looks |
| 3:01:52 | good if it's like an as then go and extract from the CID at the position |
| 3:01:57 | number four the rest of the characters so let's go and execute it and I'm |
| 3:02:02 | missing here a comma again where we don't have any Nas at the start and if |
| 3:02:07 | you scroll down you can see those as well are not affected so with that we |
| 3:02:13 | have now a nice ID to be joined with other table of course we can go and test |
| 3:02:17 | it like this where and then we take the whole thing the whole transformation and |
| 3:02:22 | say not in we remove of course the alas name we don't need it and then we make |
| 3:02:27 | very simple substring select distinct CST key the customer key from the silver |
| 3:02:34 | table can be silver CRM cost info so that's it let's go and check so as you |
| 3:02:41 | can see it is working fine so we are not able to find any unmatching data between |
| 3:02:46 | the customer info from ERB and the CRM but of course after the transformation |
| 3:02:51 | if you don't use the transformation so if I just remove it like this we will |
| 3:02:54 | find a lot of unmatching data so this means our transformation is working |
| 3:02:59 | perfectly and we can go and remove the original value so that's it for the |
| 3:03:03 | First Column okay now moving on to the next field we have the birthday of their |
| 3:03:07 | customers so the first thing to do is to check the data type it is a date so it's |
| 3:03:11 | fine it is not an integer or a string so we don't have to convert anything but |
| 3:03:16 | still there is something to check with the birth dates so we can check whether |
| 3:03:19 | we have something out of range so for example we can go and check whether we |
| 3:03:23 | have really old dates at the birth dates so let's take 1900 and let's say 24 and |
| 3:03:30 | we can take the first date of the month so let's go and check that well it looks |
| 3:03:34 | like that we have customers that are older than a 100 Year well I don't know |
| 3:03:38 | maybe this is correct but it sounds of course strange to bit of the business of |
| 3:03:43 | course this is Creed and he is in charge of |
| 3:03:48 | something that is correct say hi to the kids hi kids yay and then we can go and |
| 3:03:53 | check the other boundary where it is almost impossible to have a customer |
| 3:03:58 | that the birthday is in the future so we can say birth date is higher than the |
| 3:04:04 | current dates like this so let's go and query this information well it will not |
| 3:04:09 | work because we have to have like an or between them and now if we check the |
| 3:04:12 | list over here we have dates that are invalid for the birth dates so all those |
| 3:04:18 | dates they are all birthday in the future and this is totally unacceptable |
| 3:04:23 | so this is an indicator for bad data quality of course you can go and report |
| 3:04:26 | it to the source system in order to correct it so here it's up to you what |
| 3:04:29 | to do with those dates either leave it as it is as a bad data or we can go and |
| 3:04:34 | clean that up by replacing all those dates with a null or maybe replacing |
| 3:04:38 | only the one that is Extreme where it is 100% is incorrect so let's go and write |
| 3:04:44 | the transformation for that as usual we're going to start with case whenn per |
| 3:04:48 | dates is larger than the current date and time then null otherwise we can have |
| 3:04:55 | an else where we have the birth dat as it is and then we have an end as birth |
| 3:05:01 | date so let's go and excuse it and with that we should not get any customer we |
| 3:05:07 | the birthday in the future so that's it for the birth dates now let's move to |
| 3:05:12 | the next one we have the gender now again the gender informations is |
| 3:05:15 | localities so we have to go and check all the possible values inside this |
| 3:05:19 | column so in order to check all the possible values we're going to use |
| 3:05:23 | select distinct gen from our table so let's go and execute it and now the data |
| 3:05:28 | doesn't look really good so we have here a null we have an F we have here an |
| 3:05:33 | empty string we have male female and again we have the m so this is not |
| 3:05:38 | really good what we going to do we're going to go and clean up all those |
| 3:05:40 | informations in order to have only three values male female and not available so |
| 3:05:46 | we're going to do it like this we're going to say case when and now we're |
| 3:05:48 | going to go and trim the values just to make sure there is like no empty spaces |
| 3:05:53 | and as well I'm going to go and use the upper function just to make sure that in |
| 3:05:57 | the future if we get any lower cases and so on we are covering all the different |
| 3:06:01 | scenarios so case this is in F4 let's say |
| 3:06:07 | female then make it as female and we can go and do the same thing for the male |
| 3:06:14 | like this so if it is an M or a male make sure it is capital letters because |
| 3:06:19 | here we are using the upper then it is a male otherwise all other scenarios it |
| 3:06:24 | should be not available so whether it is an empty string or nulls and so on so we |
| 3:06:29 | have to have an end of course as gen so now let's go and test it and check |
| 3:06:34 | whether we have covered everything so you can see the m is now male the empty |
| 3:06:38 | is not available the f is female the empty string or maybe spaces here is not |
| 3:06:43 | available female going to stay as it is and the same for the male so with that |
| 3:06:47 | we are covering all the scenarios and we are following our standards in the |
| 3:06:51 | project so I'm going to go and cut this and put it in our original query over |
| 3:06:56 | here so let's go and execute the whole thing and with that we have cleaned up |
| 3:07:01 | all those three columns now the question is did we change anything in the ddl |
| 3:07:05 | well we didn't change anything we didn't introduce any new column or change any |
| 3:07:09 | data type so that means the next step is we're going to go and insert it in the |
| 3:07:13 | server layer so as usual we're going to say here insert into silver Erp the |
| 3:07:20 | customer and then we're going to go and list all the column names so C ID birth |
| 3:07:24 | dat and the gender all right so let's go and execute it and with that we can see |
| 3:07:30 | it inserted all the data and of course the very important step as the next is |
| 3:07:34 | to check that data quality so let's go back to our query over here and change |
| 3:07:38 | it from bronze to Silver so let's go and check the silver layer well of course we |
| 3:07:42 | are getting those very old customers but we didn't change that we only change the |
| 3:07:48 | birthday that is in the future and we don't see it here in the results so that |
| 3:07:52 | means everything is clean so for the next one let's go and check the |
| 3:07:55 | different genders and as you can see we have only those three values and of |
| 3:08:00 | course we can go and take a final look to our table so you can see the C ID |
| 3:08:04 | here the birth date the gender and then we see our metadata column and |
| 3:08:08 | everything looks amazing so that's it what are the different types of data |
| 3:08:12 | Transformations that we have done first with the ID what you have done we have |
| 3:08:16 | handled inv valid values so we have removed this part where it is not needed |
| 3:08:21 | and the same thing goes for the birth dates we have handled as well invalid |
| 3:08:25 | values and then for the last one for the gender we have done data normalizations |
| 3:08:30 | by mapping the code to more friendly value and as well we have handled the |
| 3:08:34 | missing values so those are the types that we have done in this |
| 3:08:41 | code okay moving on to the second table we have the location informations so we |
| 3:08:46 | have Erp location a101 so now here the task is easy |
| 3:08:50 | because we have only two columns and if you go and check the integration model |
| 3:08:54 | we can find our table over here so we can go and connect it together with the |
| 3:08:58 | customer info from the other system using the CI ID with the customer key so |
| 3:09:03 | those two informations must be matching in order to join the tables so that |
| 3:09:07 | means we have to go and check the data so let's go and select the data CST key |
| 3:09:13 | from let's go and get the silver Data customer info so let's now if you go and |
| 3:09:18 | check the result you can see over here that we have an issue with the CI ID |
| 3:09:23 | there is like a minus between the characters and the numbers but the |
| 3:09:26 | customer ID the customer number we don't have anything that splits the characters |
| 3:09:31 | with the numbers so if you go and join those two informations it will not be |
| 3:09:34 | working so what we have to do we have to go and get rid of this minus because it |
| 3:09:38 | is totally unnecessary so let's go and fix that it's going to be very simple so |
| 3:09:42 | what we're going to do we're going to say C ID so we're going to go and search |
| 3:09:46 | for the m and replace it with nothing it's very |
| 3:09:50 | simple like this so let's go and quer it again and with that things looks very |
| 3:09:54 | similar to each others and as well we can go and query it so we're going to |
| 3:09:58 | say where our transformation is not in then we can go |
| 3:10:02 | and use this as a subquery like this so let's go and execute it and as you can |
| 3:10:08 | see we are not finding any unmatching data now so that means our |
| 3:10:11 | transformation is working and with that we can go and connect those two tables |
| 3:10:15 | together so if I take take the transformation away you can see that we |
| 3:10:19 | will find a lot of unmatching data so the transformation is okay we're going |
| 3:10:23 | to stay with it and now let's speak about the countries now we have here |
| 3:10:27 | multiple values and so on what I'm going to do this is low cardinality and we |
| 3:10:31 | have to go and check all possible values inside this column so that means we are |
| 3:10:36 | checking whether the data is consistent so we can do it like this distinct the |
| 3:10:42 | country from our table I'm just going to go and copy it like this and as well I'm |
| 3:10:46 | going to go s the data by the country so let's go and check the informations now |
| 3:10:52 | you can see we have a null we have an empty string which is really bad and |
| 3:10:56 | then we have a full name of country and then we have as well an abbreviation of |
| 3:11:01 | the countries well this is a mix this is not really good because sometimes we |
| 3:11:05 | have the E and sometimes we have Germany and then we have the United Kingdom and |
| 3:11:10 | then for the United States we have like three versions of the same information |
| 3:11:14 | which is as well not really good so the quality of the is not really good so |
| 3:11:19 | let's go and work on the transformation as usual we're going to start with the |
| 3:11:22 | case win if trim country is equal to D then we're going |
| 3:11:29 | to transform it to Germany and the next one it's going to be about the USA so if |
| 3:11:34 | trim country is in so now let's go and get those two values the US and the USA |
| 3:11:41 | so us and USA then it's going to be the United States States states so with that |
| 3:11:49 | we have covered as well those three cases now we have to talk about the null |
| 3:11:53 | and the empty string so we're going to say when trim country is equal to empty |
| 3:11:59 | string or country is null then it's going to be not available otherwise I |
| 3:12:07 | would like to get the country as it is so trim country just to make sure that |
| 3:12:11 | we don't have any leading or trailing spaces so that's it let's go and say |
| 3:12:16 | this is the country so it is working and the country information is transformed |
| 3:12:22 | and now what I'm going to do I'm going to take the whole new transformation and |
| 3:12:25 | compare it to the old one let me just call this as old country and let's go |
| 3:12:31 | and query it so now we can check those value State as before so nothing did |
| 3:12:35 | change the de is now Germany the empty string is not available the null the |
| 3:12:40 | same thing and the United Kingdom State as like it's like before and now we have |
| 3:12:46 | one value for all those information so it's only the United States so it looks |
| 3:12:51 | perfect and with that we have cleaned as well the second column so with that we |
| 3:12:55 | have now clean results and now the question did we change anything in the |
| 3:12:58 | ddl well we haven't changed anything both of them are varar so we can go now |
| 3:13:03 | immediately and insert it into our table so insert into silver customer location |
| 3:13:09 | and here we have to specify the columns it's very simple the ID and the country |
| 3:13:14 | so let's go and execute it and as you can see we got now inserted all those |
| 3:13:19 | values of course as a next we go and double check those informations I would |
| 3:13:23 | just go and remove all those stuff as well here and instead of bronze let's go |
| 3:13:28 | with the silver so as you can see all the values of the country looks good and |
| 3:13:33 | let's have a final look to the table so like this so we have the IDS without the |
| 3:13:38 | separator we have the countries and as well our metadata information so with |
| 3:13:43 | that we have cleaned up the data for the location okay so now what are the |
| 3:13:46 | different types of data transformation that we have done here is first we have |
| 3:13:50 | handled invalid values so we have removed the minus with an empty string |
| 3:13:54 | and for the country we have done data normalization so we have replaced codes |
| 3:13:59 | with friendly values and as well at the same time we have handled missing values |
| 3:14:04 | by replacing the empty string and null with not available and one more thing of |
| 3:14:09 | course we have removed the unwanted spaces so those are the different types |
| 3:14:13 | of transformation that we have done for this table |
| 3:14:20 | okay guys now keep the energy up keep the spirit up we have to go and clean up |
| 3:14:24 | the last table in the bronze layer and of course we cannot go and Skip anything |
| 3:14:28 | we have to check the quality and to detect all the errors so now we have a |
| 3:14:32 | table about the categories for the products and here we have like four |
| 3:14:36 | columns let's go and start with the first one the ID as you can see in our |
| 3:14:40 | integration model we can connect this table together with the product info |
| 3:14:44 | from the CRM using the product key and as as you remember in the silver layer |
| 3:14:48 | we have created an extra column for that in the product info so if you go and |
| 3:14:52 | select those data you can see we have a column called category ID and this one |
| 3:14:57 | is exactly matching the ID that we have in this table and we have done the |
| 3:15:02 | testing so this ID is ready to be used together with the other table so there |
| 3:15:07 | is nothing to do over here and now for the next columns they are string and of |
| 3:15:11 | course we can go and check whether there are any unwanted spaces so we are |
| 3:15:15 | checking for The Unwanted spaces is so let's go and check select star from and |
| 3:15:20 | we're going to go and get the same table like this here and first we are checking |
| 3:15:24 | the category so the category is not equal to the category after trimming The |
| 3:15:30 | Unwanted spaces so let's go and execute it and as you can see we don't have any |
| 3:15:35 | results so there are no unwanted spaces let's go and check the other column for |
| 3:15:39 | example the subcategory the next one so let's get the subcategory and the under |
| 3:15:45 | query as well we don't have anything so that means we don't have unwanted spaces |
| 3:15:50 | for the subcategory let's go now and check the last column so I will just |
| 3:15:54 | copy and paste now let's get the maintenance and let's go and execute and |
| 3:15:59 | as well no results perfect we don't have any unwanted spaces inside this table so |
| 3:16:04 | now the next step is that we're going to go and check the data standardizations |
| 3:16:08 | because all those columns has low cardinality so what we're going to do |
| 3:16:11 | we're going to say select this thing let's get the cat |
| 3:16:16 | category from our table I'll just copy and paste it and check all values so as |
| 3:16:21 | you can see we have the accessories bikes clothing and components everything |
| 3:16:26 | looks perfect we don't have to change anything in this column let's go and |
| 3:16:29 | check the subcategory and if you scroll down all values are friendly and nice as |
| 3:16:35 | well nothing to change here and let's go and check the last column the |
| 3:16:39 | maintenance perfect we have only two values yes and no we don't have any |
| 3:16:43 | nulls so my friends that means this table has really nice data quality and |
| 3:16:48 | we don't have to clean up anything but still we have to follow our process we |
| 3:16:52 | have to go and load it from the bronze to the silver even if we didn't |
| 3:16:56 | transform anything so our job is really easy here we're going to go and say |
| 3:17:00 | insert into silver dots Erp PX and so on and we're going to go and Define The |
| 3:17:07 | Columns so it's going to be the ID the category sub category maintenance so |
| 3:17:13 | that's it let's go and insert the data now as usual what we're going to do |
| 3:17:16 | we're going to go and check the data so silver Erp PX let's have a look all |
| 3:17:23 | right so we can see the IDS are here the categories the subcategories the |
| 3:17:27 | maintenance and we have our meta column so everything is inserted correctly all |
| 3:17:33 | right so now I have all those queries and the insert statements for all six |
| 3:17:38 | tables and now what is important before inserting any data we have to make sure |
| 3:17:42 | that we are trating and emptying the table because if you run this qu twice |
| 3:17:47 | what's going to happen you will be inserting duplicates so first truncate |
| 3:17:51 | the data and then do a full load insert all data so we're going to have one step |
| 3:17:56 | before it's like the bronze layer we're going to say trate table and then we |
| 3:17:59 | will be trating the silver customer info and only after that we have to go and |
| 3:18:04 | insert the data and of course we can go and give this nice information at the |
| 3:18:08 | start so first we are truncating the table and then inserting so if I go and |
| 3:18:13 | run the whole thing so let's go and do it it will be working so if I can run it |
| 3:18:17 | again we will not have any duplicates so we have to go and add this tip before |
| 3:18:21 | each insert so let's go and do that all right so I'm done with all tables so now |
| 3:18:27 | let's go and run everything so let's go and execute it and we can see in the |
| 3:18:32 | messaging everything working perfectly so with that we made all tables empty |
| 3:18:36 | and then we inserted the |
| 3:18:41 | data so perfect with that we have a nice script that loads the silver layer but |
| 3:18:46 | of course like the bronze layer we're going to put everything in one stored |
| 3:18:50 | procedure so let's go and do that we'll go to the beginning over here and say |
| 3:18:54 | create or alter procedure and we're going to put it in the schema silver and |
| 3:19:00 | using the naming convention load silver and we're going to go over here and say |
| 3:19:03 | begin and take the whole code end it is long one and give it one push with a tab |
| 3:19:09 | and then at the end we're going to say and perfect so we have our s procedure |
| 3:19:14 | but we forgot here the US with that we will not have any error let's go and |
| 3:19:18 | execute it so the thir procedure is created if you go to the programmability |
| 3:19:23 | and you will find two procedures load bronze and load silver so now let's go |
| 3:19:27 | and try it out all what you have to do is now only to execute the Silver Load |
| 3:19:32 | silver so let's execute the start procedure and with that we will get the |
| 3:19:37 | same results this thir procedure now is responsible of loading the whole silver |
| 3:19:42 | layer now of course the messaging here is not really good because we have |
| 3:19:47 | learned in the bronze layer we can go and add many stuff like handling the |
| 3:19:51 | error doing nce messaging catching the duration time so now your task is to |
| 3:19:56 | pause the video take this thir procedure and go and transform it to be very |
| 3:20:01 | similar to the bronze layer with the same messaging and all the add-ons that |
| 3:20:05 | we have added so pause the video now I will do it as well offline and I will |
| 3:20:09 | see you |
| 3:20:14 | soon okay so I hope you are done and I can show you the results it's like the |
| 3:20:19 | bronze layer we have defined at the star few variables in order to catch the |
| 3:20:23 | duration so we have the start time the end time patch start time and Patch end |
| 3:20:28 | time and then we are printing a lot of stuff in order to have like nice |
| 3:20:31 | messaging in the outut so at the start we are saying loading the server layer |
| 3:20:36 | and then we start splitting by The Source system so loading the CRM tables |
| 3:20:40 | and I'm going to show you only one table for now so we are setting the timer so |
| 3:20:44 | we are saying start time get the dat date and time informations to it then we |
| 3:20:48 | are doing the usual we are truncating the table and then we are inserting the |
| 3:20:52 | new informations after cleaning it up and we have this nice message where we |
| 3:20:56 | say load duration where we are finding the differences between the start time |
| 3:21:00 | and the end time using the function dat diff and we want to show the result in |
| 3:21:05 | the seconds so we are just printing how long it took to load this table and |
| 3:21:10 | we're going to go and repeat this process for all the tables and of course |
| 3:21:14 | we are putting everything in try and Cat so the SQL going to go and try to |
| 3:21:18 | execute the tri part and if there are any issues the SQL going to go and |
| 3:21:23 | execute the catch and here we are just printing few information like the error |
| 3:21:27 | message the error number and the error States and we are following exactly the |
| 3:21:31 | same standard at the bronze layer so let's go and execute the whole thing and |
| 3:21:37 | with that we have updated the definition of the S procedure let's go now and |
| 3:21:40 | execute it so execute silver do load silver so let's go and do that it went |
| 3:21:47 | very fast like few than 1 second again because we are working on local machine |
| 3:21:51 | loading the server layer loading the CRM tables and we can see this nice |
| 3:21:56 | messaging so it start with trating the table inserting the data and we are |
| 3:22:00 | getting the load duration for this table and you will see that everything is |
| 3:22:04 | below 1 second and that's because at in real project you will get of course more |
| 3:22:08 | than 1 second so at the end we have low duration of the whole silver layer and |
| 3:22:13 | now I have one more thing for you let's say that you are changing the design of |
| 3:22:18 | this thr procedure for the silver layer you are adding different types of |
| 3:22:21 | messaging or maybe are creating logs and so on so now all those new ideas and |
| 3:22:26 | redesigns that you are doing for the silver layer you have always to think |
| 3:22:30 | about bringing the same changes as well in the other store procedure for the |
| 3:22:34 | pron layer so always try to keep your codes following the same standards don't |
| 3:22:39 | have like one idea in One S procedure and an old idea in another one always |
| 3:22:44 | try to maintain those scripts and to keep them all up to date following the |
| 3:22:48 | same standards otherwise it can to be really hard for other developers to |
| 3:22:52 | understand the cause I know that needs a lot of work and commitments but this is |
| 3:22:56 | your job to make everything following the best practices and following the |
| 3:23:00 | same naming convention and standards that you put for your projects so guys |
| 3:23:04 | now we have very nice two ETL scripts one that loads the pron layer and |
| 3:23:09 | another one for the server layer so now our data bear house is very simple all |
| 3:23:13 | what you have to do is to run first the bronze layer and with that we are taking |
| 3:23:17 | all the data from the CSV files from the source and we put it inside our data |
| 3:23:22 | warehouse in the pron layer and with that we are refreshing the whole bronze |
| 3:23:26 | layer once it's done the next step is to run the start procedure of the servey |
| 3:23:31 | layer so once you executed you are taking now all the data from the bronze |
| 3:23:35 | layer transforming it cleaning it up and then loading it to the server layer and |
| 3:23:41 | as you can see the concept is very simple we are just moving the data from |
| 3:23:44 | one layer another layer with different tasks all right guys so as you can see |
| 3:23:48 | in the silver layer we have done a lot of data Transformations and we have |
| 3:23:52 | covered all the types that we have in the data cleansing so we remove |
| 3:23:56 | duplicates data filtering handling missing data invalid data unwanted |
| 3:24:00 | spaces casting the data types and so on and as well we have derived new columns |
| 3:24:05 | we have done data enrichment and we have normalized a lot of data so now of |
| 3:24:09 | course what we have not done yet business rules and logic data |
| 3:24:13 | aggregations and data integration this is for the next layer all right my |
| 3:24:17 | friends so finally we are done cleaning up the data and checking the quality of |
| 3:24:22 | our data so we can go and close those two steps and now to the next step we |
| 3:24:26 | have to go and extend the data flow diagram so let's |
| 3:24:32 | go okay so now let's go and extend our data flow for the silver layer so what |
| 3:24:38 | I'm going to do I'm just going to go and copy the whole thing and put it side by |
| 3:24:43 | side to the bronze layer and let's call it silver |
| 3:24:46 | layer and the table names going to stay as before because we have like one to |
| 3:24:51 | one like the bronze layer but what we're going to do we're going to go and change |
| 3:24:54 | the coloring so I'm going to go and Mark everything and make it gray like silver |
| 3:24:59 | and of course what is very important is to make the lineage so I'm going to go |
| 3:25:02 | now from the bronze and take an arrow and put it to the server table and now |
| 3:25:08 | with that we have like a lineage between three layers and you are checking this |
| 3:25:11 | table the customer info you can understand aha this comes from the |
| 3:25:15 | bronze layer from the customer info and as well this comes from the source |
| 3:25:19 | system CRM so now you can see the lineage between different layers and |
| 3:25:24 | without looking to any scripts and so on in one picture you can understand the |
| 3:25:28 | whole projects so I don't have to explain a lot of stuff by just looking |
| 3:25:32 | to this picture you can understand how the data is Flowing between sources |
| 3:25:37 | bronze layer silver layer and to the gold layer of course later so as you can |
| 3:25:41 | see it looks really nice and clean all right so with that we have updated the |
| 3:25:45 | data flow next we're going to go and commit our |
| 3:25:48 | work in the get repo so let's |
| 3:25:53 | go okay so now let's go and commit our scripts we're going to go to the folder |
| 3:25:58 | scripts and here we have a server layer if you don't have it of course you can |
| 3:26:01 | go and create it so first we're going to go and put the ddl scripts for the |
| 3:26:05 | server layer so let's go and I will paste the code over here and as usually |
| 3:26:10 | we have this comment at the header explaining the purpose of this scripts |
| 3:26:14 | so let's go and commit our work work and we're going to do the same thing for the |
| 3:26:18 | start procedure that loads the silver layer so I'm going to go over here I |
| 3:26:23 | have already file for that so let's go and paste that so we have here our |
| 3:26:27 | stored procedures and as usual at the start we have as well so this script is |
| 3:26:31 | doing the ETL process where we load the data from bronze into silver so the |
| 3:26:36 | action is to truncate the table first and then insert transformed cleans data |
| 3:26:41 | from bronze to Silver there are no parameters at all and this is how you |
| 3:26:45 | can use the start procedure okay so we're going to go and commit our work |
| 3:26:50 | and now one more thing that we want to commit in our project all those quaries |
| 3:26:54 | that you have built to check the quality of the server layer so this time we will |
| 3:26:58 | not put it in the scripts we're going to go to the tests and here we're going to |
| 3:27:01 | go and make a new file called quality checks silver and inside it we're going |
| 3:27:06 | to go and paste all the queries that we have filled I just here reorganize them |
| 3:27:11 | by the tables so here we can see all the checks that we have done during the |
| 3:27:16 | course and at the header we have here nice comments so here we are just saying |
| 3:27:20 | that this script is going to check the quality of the server layer and we are |
| 3:27:23 | checking for nulls duplicates unwanted spaces invalid date range and so on so |
| 3:27:28 | that each time you come up with a new quality check I'm going to recommend you |
| 3:27:32 | to share it with the project and with other team in order to make it part of |
| 3:27:36 | multiple checks that you do after running the atls so that's it I'm going |
| 3:27:40 | to go and put those checks in our repo and in case I come up with new check I'm |
| 3:27:45 | going to go and update it perfect so now we have our code in our repository all |
| 3:27:50 | right so with that our code is safe and we are done with the whole epic so we |
| 3:27:55 | have build the silver layer now let's go and minimize it and now we come to my |
| 3:28:00 | favorite layer the gold layer so we're going to go and build it the first step |
| 3:28:04 | as usual we have to analyze and this time we're going to explore the business |
| 3:28:07 | objects so let's |
| 3:28:12 | go all right so now we come to the big question how we going to build the gold |
| 3:28:15 | layer as usual we start with analyzing so now what we're going to do here is to |
| 3:28:19 | explore and understand what are the main business objects that are hidden inside |
| 3:28:24 | our source system so as you can see we have two sources six files and here we |
| 3:28:28 | have to identify what are the business objects once we have this understanding |
| 3:28:32 | then we can start coding and here the main transformation that we are doing is |
| 3:28:35 | data integration and here usually I split it into three steps the first one |
| 3:28:40 | we're going to go and build those business objects that we have identified |
| 3:28:43 | and after we have a business object we have to look at it and decide what is |
| 3:28:48 | the type of this table is it a dimension is it a fact or is it like maybe a flat |
| 3:28:52 | table so what type of table that we have built and the last step is of course we |
| 3:28:57 | have now to rename all the columns into something friendly and easy to |
| 3:29:01 | understand so that our consumers don't struggle with technical names so once we |
| 3:29:05 | have all those steps what we're going to do it's time to validate what we have |
| 3:29:07 | created so what we have to do the new data model that we have created it |
| 3:29:11 | should be connectable and we have to check that the data integration is done |
| 3:29:15 | correctly and once everything is fine we cannot skip the last step we have to |
| 3:29:19 | document and as well commit our work in the git and here we will be introducing |
| 3:29:24 | new type of documentations so we're going to have a diagram about the data |
| 3:29:27 | model we're going to build a data dictionary where we going to describe |
| 3:29:31 | the data model and of course we can extend the data flow diagram so this is |
| 3:29:34 | our process those are the main steps that we will do in order to build the |
| 3:29:38 | gold |
| 3:29:42 | layer okay so what is exactly data modeling usually usually the source |
| 3:29:46 | system going to deliver for you row data an organized messy not very useful in |
| 3:29:52 | its current States but now the data modeling is the process of taking this |
| 3:29:56 | row data and then organize it and structure it in meaningful way so what |
| 3:30:01 | we are doing we are putting the data in a new friendly and easy to understand |
| 3:30:06 | objects like customers orders products each one of them is focused on specific |
| 3:30:11 | information and what is very important is we're going to describe the |
| 3:30:15 | relationship between those objects so by connecting them using lines so what you |
| 3:30:19 | have built on the right side we call it logical data model if you compare to the |
| 3:30:23 | left side you can see the data model makes it really easy to understand our |
| 3:30:27 | data and the relationship the processes behind them now in data modeling we have |
| 3:30:31 | three different stages or let's say three different ways on how to draw a |
| 3:30:34 | data model the first stage is the conceptual data model here the focus is |
| 3:30:39 | only on the entity so we have customers orders products and we don't go in |
| 3:30:43 | details at all so we don't specify any columns or attributes inside those boxes |
| 3:30:48 | we just want to focus what are the entities that we have and as well the |
| 3:30:52 | relationship between them so the conceptual data model don't focus at all |
| 3:30:56 | on the details it just gives the big picture so the second data model that we |
| 3:31:00 | can build is The Logical data model and here we start specifying what are the |
| 3:31:05 | different columns that we can find in each entity like we have the customer ID |
| 3:31:09 | the first name last name and so on and we still draw the relationship between |
| 3:31:13 | those entities and as well we make it clear which columns are the primary key |
| 3:31:17 | and so on so as you can see we have here more details but one thing we don't |
| 3:31:20 | describe a lot of details for each column and we are not worry how exactly |
| 3:31:25 | we going to store those tables in the database the third and last stage we |
| 3:31:29 | have the physical data model this is where everything gets ready before |
| 3:31:33 | creating it in the database so here you have to add all the technical details |
| 3:31:37 | like adding for each column the data types and the length of each data type |
| 3:31:42 | and many other database techniques and details so again if if you look to the |
| 3:31:46 | conceptual data model it gives us the big picture and in The Logical data |
| 3:31:50 | model we dive into details of what data we need and the physical layer model |
| 3:31:54 | prepares everything for the implementation in the database and to be |
| 3:31:58 | honest in my projects I only draw the conceptual and The Logical data model |
| 3:32:03 | because drawing and building the physical data model needs a lot of |
| 3:32:06 | efforts and time and there are many tools like in data bricks they |
| 3:32:10 | automatically generate those models so in this project what we're going to do |
| 3:32:13 | we're going to draw The Logical data model for the gold |
| 3:32:20 | layer all right so now for analytics and specially for data warehousing and |
| 3:32:24 | business intelligence we need a special data model that is optimized for |
| 3:32:28 | reporting and analytics and it should be flexible scalable and as well easy to |
| 3:32:33 | understand and for that we have two special data models the first type of |
| 3:32:37 | data model we have the star schema it has a central fact table in the middle |
| 3:32:41 | and surrounded by Dimensions the fact table contains transactions events and |
| 3:32:46 | the dimensions contains descriptive informations and the relationship |
| 3:32:50 | between the fact table in the middle and the dimensions around it forms like a |
| 3:32:54 | star shape and that's why we call it star schema and we have another data |
| 3:32:58 | model called snowflake schema it looks very similar to the star schema so we |
| 3:33:02 | have again the fact in the middle and surrounded by Dimensions but the big |
| 3:33:06 | difference is that we break the dimensions into smaller subdimensions |
| 3:33:11 | and the shape of this data model as you are extending the dimensions it's going |
| 3:33:15 | to look like a snowflake so now if you compare them side by side you can see |
| 3:33:19 | that the star schema looks easier right so it is usually easy to understand easy |
| 3:33:23 | to query it is really perfect for analyzes but it has one issue with that |
| 3:33:28 | the dimension might contain duplicates and your Dimensions get bigger with the |
| 3:33:32 | time now if you compare to the snowflake you can see the schema is more complex |
| 3:33:36 | you so you need a lot of knowledge and efforts in order to query something from |
| 3:33:41 | the snowflake but the main advantage here comes with the normalization as you |
| 3:33:44 | are breaking those redundancies in small tables you can optimize the storage but |
| 3:33:49 | to be honest who care about the storage so for this project I have chose to use |
| 3:33:53 | the star schema because it is very commonly used perfect for reporting like |
| 3:33:57 | for example if you're using power pii and we don't have to worry about the |
| 3:34:01 | storage so that's why we going to adapt this model to build our gold |
| 3:34:08 | layer okay so now one more thing about those data models is that they contain |
| 3:34:12 | two types of tables fact and dimensions so when I I say this is a fact table or |
| 3:34:17 | a dimension table well the dimension contains descriptive informations or |
| 3:34:21 | like categories that gives some context to your data for example a product info |
| 3:34:26 | you have product name category subcategories and so on this is like a |
| 3:34:29 | table that is describing the product and this we call it Dimension but in the |
| 3:34:34 | other hand we have facts they are events like transactions they contain three |
| 3:34:39 | important informations first you have multiple IDs from multiple dimensions |
| 3:34:44 | then we have like the informations like when the transaction or the event did |
| 3:34:49 | happen and the third type of information you're going to have like measures and |
| 3:34:52 | numbers so if you see those three types of data in one table then this is a fact |
| 3:34:57 | so if you have a table that answers how much or how many then this is a fact but |
| 3:35:02 | if you have a table that answers who what where then this is a dimension |
| 3:35:07 | table so this is what dimension and fact |
| 3:35:13 | tables all right my friends so so far in the bronze layer and in the silver layer |
| 3:35:18 | we didn't discuss anything about the business so the bronze and silver were |
| 3:35:22 | very technical we are focusing on data Eng gestion we are focusing on cleaning |
| 3:35:26 | up the data quality of the data but still the tables are very oriented to |
| 3:35:30 | the source system now comes the fun part in the god layer where we're going to go |
| 3:35:34 | and break the whole data model of the sources so we're going to create |
| 3:35:38 | something completely new to our business that is easy to consume for business |
| 3:35:43 | reporting and analyzes and here it is very very important to have a clear |
| 3:35:47 | understanding of the business and the processes and if you don't know it |
| 3:35:50 | already at this phase you have really to invest time by meeting maybe process |
| 3:35:54 | experts the domain experts in order to have clear understanding what we are |
| 3:35:59 | talking about in the data so now what we're going to do we're going to try to |
| 3:36:02 | detect what are the business objects that are hidden in the source systems so |
| 3:36:07 | now let's go and explore that all right now in order to build a new data model I |
| 3:36:11 | have to understand first the original data model what are the main business |
| 3:36:15 | objects that we have how things are related to each others and this is very |
| 3:36:19 | important process in building a new model so now what I usually do I start |
| 3:36:23 | giving labels to all those tables so if you go to the shapes over here let's go |
| 3:36:27 | and search for label and if you go to more icons I'm going to go and take this |
| 3:36:32 | label over here so drag and drop it and then I'm going to go and increase maybe |
| 3:36:36 | the size of the font so let's go with 20 and bold just make it a little bit |
| 3:36:41 | bigger so now by looking to this data model we can see that we have a bradu |
| 3:36:45 | for informations in the CRM and as well in the ARP and then we have like |
| 3:36:49 | customer informations and transactional table so now let's focus on the product |
| 3:36:54 | so the product information is over here we have here the current and the history |
| 3:36:58 | product informations and here we have the categories that's belong to the |
| 3:37:02 | products so in our data model we have something called products so let's go |
| 3:37:06 | and create this label it's going to be the products and so let's go and give it |
| 3:37:10 | a color to the style let's Pi for example the red one now let's go and |
| 3:37:15 | move this label and put it beneath this table over here that I have like a label |
| 3:37:20 | saying this table belongs to the objects called products now I'm going to do the |
| 3:37:25 | same thing for the other table over here so I'm going to go and tag this table to |
| 3:37:29 | the product as well so that I can see easily which tables from the sources |
| 3:37:33 | does has informations about the product business object all right now moving on |
| 3:37:38 | we have here a table called customer information so we have a lot of |
| 3:37:41 | information about the customer we have as well in the ARB customer information |
| 3:37:45 | where we have the birthday and the country so those three tables has to do |
| 3:37:49 | with the object customer so that means we're going to go and label it like that |
| 3:37:53 | so let's call it customer and I'm going to go and pick different color for that |
| 3:37:58 | let's go with the green so I will tag this table like this and the same thing |
| 3:38:03 | for the other tables so copy tag the second table and the third table now it |
| 3:38:09 | is very easily for me to see which table to belong to which business objects and |
| 3:38:13 | now we have the final table over here and only one table about the sales and |
| 3:38:18 | orders in the ARB we don't have any informations about that so this one |
| 3:38:22 | going to be easy let's call it sales and let's move it over here and as well |
| 3:38:27 | maybe change the color of that to for example this color over here now this |
| 3:38:32 | step is very important by building any data model in the gold layer it gives |
| 3:38:35 | you a big picture about the things that you are going to module so now the next |
| 3:38:39 | step with that we're going to go and build those objects step by step so |
| 3:38:42 | let's start with the first objects with our customers so here we we have three |
| 3:38:45 | tables and we're going to start with the CRM so let's start with this table over |
| 3:38:49 | here all right so with that we know what are our business objects and this task |
| 3:38:54 | is done and now in The Next Step we're going to go back to SQL and start doing |
| 3:38:58 | data Integrations and building completely new data model so let's go |
| 3:39:02 | and do |
| 3:39:06 | that now let's have a quick look to the gold layer specifications so this is the |
| 3:39:11 | final stage we're going to provide data to be consumed by reporting and |
| 3:39:14 | Analytics and this time we will not be building tables we will be using views |
| 3:39:19 | so that means we will not be having like start procedure or any load process to |
| 3:39:23 | the gold layer all what you are doing is only data transformation and the focus |
| 3:39:28 | of the data transformation going to be data integration aggregation business |
| 3:39:31 | logic and so on and this time we're going to introduce a new data model we |
| 3:39:35 | will be doing star schema so those are the specifications for the gold layer |
| 3:39:40 | and this is our scope so this time we make sure that we are selecting data |
| 3:39:44 | from the silver layer not from the bronze because the bronze |
| 3:39:48 | has bad data quality and the server is everything is prepared and cleaned up in |
| 3:39:52 | order to build the good layer going to be targeting the server layer so let's |
| 3:39:56 | start with select star from and we're going to go to the silver CRM customer |
| 3:40:02 | info so let's go and hit execute and now we're going to go and select the columns |
| 3:40:06 | that we need to be presented in the gold layer so let's start selecting The |
| 3:40:10 | Columns that we want we have the ID the key the first name |
| 3:40:19 | I will not go and get the metadata information this only belongs to the |
| 3:40:23 | Silver Perfect the next step is that I'm going to go and give this table an ilas |
| 3:40:27 | so let's go and call it CI and I'm going to make sure that we are selecting from |
| 3:40:32 | this alas because later we're going to go and join this table with other tables |
| 3:40:36 | so something like this so we're going to go with those columns now let's move to |
| 3:40:39 | the second table let's go and get the birthday information so now we're going |
| 3:40:43 | to jump to the other system and we have to join the data by the CI ID together |
| 3:40:48 | with the customer key so now we have to go and join the data with another table |
| 3:40:52 | and here I try to avoid using the inner join because if the other table doesn't |
| 3:40:57 | have all the information about the customers I might lose customers so |
| 3:41:01 | always start with the master table and if you join it with any other table in |
| 3:41:05 | order to get informations try always to avoid the inner join because the other |
| 3:41:10 | source might not have all the customers and if you do inner join you might lose |
| 3:41:14 | customers so iend to start from the master table and then everything else is |
| 3:41:18 | about the lift join so I'm going to say Lift join silver Erp customer a z12 so |
| 3:41:24 | let's give it the ls CA and now we have to join the tables so it's going to be |
| 3:41:28 | by C from the first table it going to be the customer key equal to ca and we have |
| 3:41:35 | the CI ID now of course we're going to get matching data because we checked the |
| 3:41:39 | silver layer but if we haven't prepared the data in the silver layer we have to |
| 3:41:43 | do here preparation step in order to join Jo the tables but we don't have to |
| 3:41:46 | do that because that was a preep in the silver layer so now you can see the |
| 3:41:50 | systematic that we have in this pron silver gold so now after joining the |
| 3:41:55 | tables we have to go and pick the information that we need from the second |
| 3:41:58 | table which is the birth dat so B dat and as well from this table there is |
| 3:42:04 | another nice information it is the gender information so that's all what we |
| 3:42:09 | need from the second table let's go and check the third table so the third table |
| 3:42:14 | is about the location information the countries and as well we connect the |
| 3:42:18 | tables by the C ID with the key so let's go and do that we're going to say as |
| 3:42:22 | well left join silver Erp location and I'm going to give it the name LA and |
| 3:42:28 | then we have to join while the keys the same thing it's going to be CI customer |
| 3:42:33 | key equal to La a CI ID again we have prepared those IDs and keys in the |
| 3:42:39 | server layer so the joint should be working now we have to go and pick the |
| 3:42:43 | data from the second table so what do we we have over here we have the ID the |
| 3:42:47 | country and the metadata information so let's go and just get the country |
| 3:42:51 | perfect so now with that we have joined all the three tables and we have picked |
| 3:42:55 | all the columns that we want in this object so again by looking over here we |
| 3:43:00 | have joined this table with this one and this one so with that we have collected |
| 3:43:04 | all the customer informations that we have from the two Source systems okay so |
| 3:43:09 | now let's go and query in order to make sure that we have everything correct and |
| 3:43:12 | in order to understand that your joints are correct you have to keep your eye in |
| 3:43:17 | those three columns so if you are seeing that you are getting data that means you |
| 3:43:21 | are doing the the joints correctly but if you are seeing a lot of nulls or no |
| 3:43:26 | data at all that means your joints are incorrect but now it looks for me it is |
| 3:43:31 | working and another check that I do is that if your first table has no |
| 3:43:36 | duplicates what could happen is that after doing multiple joints you might |
| 3:43:40 | now start getting dgates because the relationship between those tables is not |
| 3:43:44 | clear one to one you might get like one to many relationship or many to many |
| 3:43:48 | relationships so now the check that I usually do at this stage advance I have |
| 3:43:52 | to make sure that I don't have duplicates from their results so we |
| 3:43:56 | don't have like multiple rows for the same customer so in order to do that we |
| 3:44:00 | go and do a quick group bu so we're going to group by the data by the |
| 3:44:05 | customer ID and then we do the counts from this subquery so this is the |
| 3:44:11 | whole subquery and then after that we're going to go and say Group by the |
| 3:44:17 | customer ID and then we say having counts higher than one so this query |
| 3:44:25 | actually try to find out whether we have any duplicates in the primary key so |
| 3:44:30 | let's go and executed we don't have any duplicate and that means after joining |
| 3:44:35 | all those tables with the customer info those tables didn't didn't cause any |
| 3:44:39 | issues and it didn't duplicate my data so this is very important check to make |
| 3:44:44 | sure that you are in the right way all right so that means everything is fine |
| 3:44:48 | about the D Kates we don't have to worry about it now we have here an integration |
| 3:44:53 | issue so let's go and execute it again and now if you look to the data we have |
| 3:44:56 | two sources for the gender informations one comes from the CRM and another where |
| 3:45:01 | come from the Erp so now the question is what are we going to do with this well |
| 3:45:04 | we have to do data integration so let me show you how I do it first I go and have |
| 3:45:09 | a new query and then I'm going to go and remove all other stuff and I'm going to |
| 3:45:14 | leave only those two informations and use it distinct just to focus on the |
| 3:45:19 | integration and let's go and execute it and maybe as well to do an order bu so |
| 3:45:23 | let's do one and two let's go and execute it again so now here we have all |
| 3:45:27 | the scenarios and we can see sometimes there is a matching so from the first |
| 3:45:32 | table we have female and the other table we have as well female but sometimes we |
| 3:45:35 | have an issue like those two tables are giving different informations and the |
| 3:45:39 | same thing over here so this is as well an issue different informations another |
| 3:45:43 | scenario where we have a from the first table like here we have the female but |
| 3:45:47 | in the other table we have not available well this is not a problem so we can get |
| 3:45:52 | it from the first table but we have as well the exact opposite scenario where |
| 3:45:56 | from the first table the data is not available but it is available from the |
| 3:46:00 | second table and now here you might wonder why I'm getting a null over here |
| 3:46:04 | we did handle all the missing data in the silver layer and we replace |
| 3:46:07 | everything with not available so why we are still getting a null this null |
| 3:46:11 | doesn't come directly from the tables it just come because of joining tables so |
| 3:46:17 | that means there are customers in the CRM table that is not available in the |
| 3:46:22 | Erb table and if there is like no match what's going to happen we will get a |
| 3:46:27 | null from scel so this null means there was no match and that's why we are |
| 3:46:32 | getting this null it is not coming from the content of the tables and this is of |
| 3:46:36 | course an issue but now the big issue what can happen for those two scenarios |
| 3:46:40 | here we have the data but they are different and here again we have to ask |
| 3:46:44 | the experts about it what is the master here is it the CRM system or the ARP and |
| 3:46:50 | let's say from their answer going to say the master data for the customer |
| 3:46:54 | information is the CRM so that means the CRM informations are more accurate than |
| 3:47:00 | the Erp information and this is only about the customers of course so for |
| 3:47:04 | this scenario where we have female and male then the correct information is the |
| 3:47:09 | female from the First Source system the same goes over here and here we have |
| 3:47:12 | like male and female then the correct one is is the mail because this Source |
| 3:47:17 | system is the master okay so now let's go and build this business rule we're |
| 3:47:21 | going to start as usual with the case wi so the first very important rule is if |
| 3:47:25 | we have a data in the gender information from the CRM system from the master then |
| 3:47:31 | go and use it so we're going to go and check the gender information from the |
| 3:47:34 | CRM table so customer gender is not equal to not available so that means we |
| 3:47:40 | have a value male or female let me just have here a comma like this then what |
| 3:47:45 | going to happen go and use it so we're going to use the value from the master |
| 3:47:50 | CRM is the master for gender info now otherwise that means it is not available |
| 3:47:58 | from the CRM table then go and use and grab the information from the second |
| 3:48:03 | table so we're going to say ca gender but now we have to be careful this null |
| 3:48:09 | over here we have to convert it to not available as well so we're going to use |
| 3:48:13 | the Calis so if this is a null then go and use the |
| 3:48:18 | not available like this so that's it let's have an end let me just push this |
| 3:48:23 | over here so let's go and call it new chin for now let's go and excute it and |
| 3:48:28 | let's go and check the different scenarios all those values over here we |
| 3:48:33 | have data from the CRM system and this is as well represented in the new column |
| 3:48:38 | but now for the second parts we don't have data from the first system so we |
| 3:48:42 | are trying to get it from the second system so for the first one is not |
| 3:48:46 | available and then we try to get it from the Second Source system so now we are |
| 3:48:50 | activating the else well it is null and with that the CIS is activated and we |
| 3:48:55 | are replacing the null with not available for the second scenario as |
| 3:48:59 | well the first system don't have the gender information that's why we are |
| 3:49:03 | grabbing it from the second so with that we have a female and then the third one |
| 3:49:07 | the same thing we don't have information but we get it from the Second Source |
| 3:49:11 | system we have the mail and the last one it is not available in in both Source |
| 3:49:15 | systems that's why we are getting not available so with that as you can see we |
| 3:49:19 | have a perfect new column where we are integrating two different Source system |
| 3:49:24 | in one and this is exactly what we call data integration this piece of |
| 3:49:28 | information it is way better than the source CRM and as well the source ARP it |
| 3:49:34 | is more rich and has more information and this is exactly why we Tred to get |
| 3:49:39 | data from different Source system in order to get rich information in the |
| 3:49:43 | data warehouse so do we have a nice logic and as you can see it's way easier |
| 3:49:47 | to separate it in separate query in order first to build the logic and then |
| 3:49:51 | take it to the original query so what I'm going to do I'm just going to go and |
| 3:49:55 | copy everything from here and go back to our query I'm going to go and delete |
| 3:49:59 | those informations the gender and I will put our new logic over here so a comma |
| 3:50:05 | and let's go and execute so with that we have our new nice column now with that |
| 3:50:09 | we have very nice objects we don't have delates and we have integrated data |
| 3:50:13 | together so we took three three tables and we put it in one object now the next |
| 3:50:17 | step is that we're going to go and give nice friendly names the rule in the gold |
| 3:50:22 | layer that to use friendly names and not to follow the names that we get from The |
| 3:50:26 | Source system and we have to make sure that we are following the rules by the |
| 3:50:30 | naming conventions so we are following the snake case so let's go and do it |
| 3:50:34 | step by step for the first one let's go and call it the customer ID and then the |
| 3:50:39 | next one I will get rid of using keys and so on I'm going to go and call it |
| 3:50:43 | customer number because those are customer numbers then for the next one |
| 3:50:48 | we're going to call it first name without using any prefixes and the next |
| 3:50:54 | one last name and we have here marital status so I will be using the exact name |
| 3:51:01 | but without the prefix and here we just going to call it gender and this one we |
| 3:51:06 | going to call it create date and this one birth dat and the last one going to |
| 3:51:12 | be the country so let's go and execute it now as you can see the names are |
| 3:51:18 | really friendly so we have customer ID customer numbers first name last name |
| 3:51:22 | material status gender so as you can see the names are really nice and really |
| 3:51:27 | easy to understand now the next step I'm going to think about the order of those |
| 3:51:30 | columns so the first two it makes sense to have it together the first name last |
| 3:51:34 | name then I think the country is very important information so I'm going to go |
| 3:51:38 | and get it from here and put it exactly after the last name it's just nicer so |
| 3:51:43 | let's go and execute it again so the first name last name country it's always |
| 3:51:47 | nice to group up relevant columns together right so we have here the |
| 3:51:50 | status of the gender and so on and then we have the CATE date and the birth date |
| 3:51:54 | I think I'm going to go and switch the birth date with the CATE date it's more |
| 3:51:58 | important than the CATE dates like this and here not forget a comma so execute |
| 3:52:03 | again so it looks wonderful now comes a very important decision about this |
| 3:52:08 | objects is it a fact table or a dimension well as we learned Dimensions |
| 3:52:12 | hold descriptive information about an object and as you can see we have here a |
| 3:52:17 | descriptions about the customers so all those columns are describing the |
| 3:52:22 | customer information and we don't have here like transactions and events and we |
| 3:52:26 | don't have like measures and so on so we cannot say this object is a fact it is |
| 3:52:31 | clearly a dimension so that's why we're going to go and call this object the |
| 3:52:35 | dimension customer now there is one thing that if you creating a new |
| 3:52:39 | dimension you need always a primary key for the dimension of course we can go |
| 3:52:43 | over here and the depend on the primary key that we get from The Source system |
| 3:52:47 | but sometimes you can have like Dimensions where you don't have like a |
| 3:52:51 | primary key that you can count on so what we have to do is to go and generate |
| 3:52:55 | a new primary key in the data warehouse and those primary Keys we call it |
| 3:52:59 | surrogate keys serate keys are system generated unique identifier that is |
| 3:53:05 | assigned to each record to make the record unique it is not a business key |
| 3:53:10 | it has no meaning and no one in the business knows about it we only use it |
| 3:53:14 | in order to connect our data model and in this way we have more control on how |
| 3:53:19 | to connect our data model and we don't have to depend all way on the source |
| 3:53:23 | system and there are different ways on how to generate surrogate Keys like |
| 3:53:27 | defining it in the ddl or maybe using the window function row number in this |
| 3:53:32 | data warehouse I'm going to go with a simple solution where we're going to go |
| 3:53:35 | and use the window function so now in order to generate a Sur key for this |
| 3:53:40 | Dimension what we're going to do it is very simple so we're going to say row |
| 3:53:43 | number over and here if we have to order by |
| 3:53:48 | something you can order by the create date or the customer ID or the customer |
| 3:53:53 | number whatever you want but in this example I'm going to go and order by the |
| 3:53:58 | customer ID so we have to follow the naming convention that's all surate keys |
| 3:54:02 | with the key at the end as a suffix so now let's go and query those |
| 3:54:06 | informations and as you can see at the start we have a customer key and this is |
| 3:54:11 | a sequence we don't have here of course any duplicates and now this sgate key is |
| 3:54:15 | generated in the data warehouse and we going to use this key in order to |
| 3:54:20 | connect the data model so now with that our query is ready and the last step is |
| 3:54:24 | that we're going to go and create the object and as we decided all the objects |
| 3:54:28 | in the gold layer going to be a virtual one so that means we're going to go and |
| 3:54:32 | create a view so we're going to say create View gold. dim so follow damic |
| 3:54:38 | convention stand for the dimension and we're going to have the customers and |
| 3:54:42 | then after that we have us so with that everything is ready let's go and excuse |
| 3:54:47 | it it was successful let's go to the Views now and you can see our first |
| 3:54:52 | objects so we have the dimension customers in the gold layer now as you |
| 3:54:56 | know me in the next of that we're going to go and check the quality of this new |
| 3:55:00 | objects so let's go and have a new query so select star from our view temp |
| 3:55:07 | customers and now we have to make sure that everything in the right position |
| 3:55:11 | like this and now we can do different checks like the uniqueness and so on but |
| 3:55:16 | I'm worried about the gender information so let's go and have a distinct of all |
| 3:55:21 | values so as you can see it is working perfectly we have only female male and |
| 3:55:25 | not available so that's it with that we have our first new |
| 3:55:33 | dimension okay friends so now let's go and build the second object we have the |
| 3:55:38 | products so as you can see product information is available in both Source |
| 3:55:42 | systems as usual we're going to start with the CRM informations and then we're |
| 3:55:46 | going to go and join it with the other table in order to get the category |
| 3:55:50 | informations so those are the columns that we want from this table now we come |
| 3:55:54 | here to a big decision about this objects this objects contains historical |
| 3:55:58 | informations and as well the current informations now of course depend on the |
| 3:56:02 | requirement whether you have to do analysis on the historical informations |
| 3:56:05 | but if you don't have such a requirements we can go and stay with |
| 3:56:09 | only the current informations of the products so we don't have to include all |
| 3:56:12 | the history in the objects and it is anyway as we learned from the model over |
| 3:56:16 | here we are not using the primary key we are using the product key so now what we |
| 3:56:22 | have to do is to filter out the historical data and to stay only with |
| 3:56:26 | the current data so we're going to have here aware condition and now in order to |
| 3:56:30 | select the current data what we're going to do we're going to go and Target the |
| 3:56:33 | end dates if the end date is null that means it is a current data let's take |
| 3:56:38 | this example over here so you can see here we have three record for the same |
| 3:56:42 | product key and for the first two records we have here an information in |
| 3:56:46 | the end dates because it is historical informations but the last record over |
| 3:56:51 | here we have it as a null and that's because this is the current information |
| 3:56:55 | it is open and it's not closed yet so in order to select only the current |
| 3:56:59 | informations it is very simple we're going to say BRD in dat is null so if |
| 3:57:05 | you go now and execute it you will get only the current products you will not |
| 3:57:09 | have any history and of course we can go and add comment to it filter out all |
| 3:57:15 | historical data and this means of course we don't need the end date in our |
| 3:57:19 | selection of course because it is always a null so with that we have only the |
| 3:57:24 | current data now the next step that we have to go and join it with the product |
| 3:57:29 | categories from the Erp and we're going to use here the ID so as usual the |
| 3:57:34 | master information is the CRM and everything else going to be secondary |
| 3:57:38 | that's why I use the Live join just to make sure I'm not losing I'm not |
| 3:57:43 | filtering any data because if there is no match then we lose data so let's join |
| 3:57:48 | silver Erp and the category so let's call it PC and now what we're going to |
| 3:57:53 | do we're going to go and join it using the key so PN from the CRM we have the |
| 3:57:58 | category ID equal to PC ID and now we have to go and pick columns from the |
| 3:58:04 | second table so it's going to be the PC we have the category very important PC |
| 3:58:10 | we have the subcategory and we can go and get the |
| 3:58:13 | maintenance so something like this let's go and |
| 3:58:17 | query and with that we have all those columns comes from the first table and |
| 3:58:22 | those three comes from the second so with that we have collected all the |
| 3:58:25 | product informations from the two Source systems now the next step is we have to |
| 3:58:30 | go and check the quality of these results and of course what is very |
| 3:58:34 | important is to check the uniqueness so what we're going to do we're going to go |
| 3:58:38 | and have the following query I want to make sure that the product key is unique |
| 3:58:45 | because we're going to use it later in order to join the table with the sales |
| 3:58:49 | so from and then we have to have group by |
| 3:58:53 | product key and we're going to say having |
| 3:58:56 | counts higher than one so let's go and check perfect we don't have any |
| 3:59:02 | duplicates the second table didn't cause any duplicates for our join and as well |
| 3:59:07 | this means we don't have historical data and each product is only one records and |
| 3:59:12 | we don't have any duplicates so I'm really happy about that so let's go in |
| 3:59:16 | query again now of course the next step do we have anything to integrate |
| 3:59:20 | together do we have the same information twice well we don't have that the next |
| 3:59:25 | step is that we're going to go and group up the relevant informations together so |
| 3:59:29 | I'm going to say the product ID then the product key and the product name are |
| 3:59:35 | together so all those three informations are together and after that we can put |
| 3:59:39 | all the category informations together so we can have the category ID the |
| 3:59:43 | category itself the subcategory let me just query and see the results so we |
| 3:59:48 | have the product ID key name and then we have the category ID name and the |
| 3:59:53 | subcategory and then maybe as well to put the maintenance after the |
| 3:59:58 | subcategory like this and I think the product cost and the line can start |
| 4:00:02 | could stay at the end so let me just check so those three four informations |
| 4:00:07 | about the category and then we have the cost line and the start date I'm really |
| 4:00:11 | happy with that the next step we're going to go and give n names friendly |
| 4:00:14 | names for those columns so let's start with the first one this is the product |
| 4:00:19 | ID the next one going to be the product number we need the key for the surrogate |
| 4:00:25 | key later and then we have the product name and after that we have the category |
| 4:00:31 | ID and the category and this is the subcategory and then the next one going |
| 4:00:38 | to stay as it is I don't have to rename it the next one going to be the cost and |
| 4:00:43 | the line and the last one will be the start |
| 4:00:47 | dates so let's go and execute it now we can see very nicely in the output all |
| 4:00:52 | those friendly names for the columns and it looks way nicer than before I don't |
| 4:00:57 | have even to describe those informations the name describe it so perfect now the |
| 4:01:01 | next big decision is what do we have here do we have a effect or Dimension |
| 4:01:06 | what do you think well as you can see here again we have a lot of descriptions |
| 4:01:10 | about the products so all those informations are describing the business |
| 4:01:14 | object products we don't have like here transactions events a lot of different |
| 4:01:19 | keys and ideas so we don't have really here a facts we have a dimension each |
| 4:01:24 | row is exactly describing one object describing one products that's why this |
| 4:01:29 | is a dimension okay so now since this is a dimension we have to go and create a |
| 4:01:34 | primary key for it well actually the surrogate key and as we have done it for |
| 4:01:38 | the customers we're going to go and use the window function row number in order |
| 4:01:42 | to generate it over and then we have to S the data I will go with the start |
| 4:01:47 | dates so let's go with the start dates and as well the product key and we're |
| 4:01:53 | going to gra it a name products key like this so let's go and execute it with |
| 4:01:59 | that we have now generated a primary key for each product and we're going to be |
| 4:02:05 | using it in order to connect our data model all right now the next step we |
| 4:02:08 | does we're going to go and build the view so we're going to say create view |
| 4:02:13 | we're going to say go and dimension products and then ask so |
| 4:02:18 | let's go and create our objects and now if you go and refresh the views you will |
| 4:02:22 | see our second object the second dimension so we have here in the gold |
| 4:02:26 | layer the dimension products and as usual we're going to go and have a look |
| 4:02:30 | to this view just to make sure that everything is fine so them products so |
| 4:02:37 | let's execute it and by looking to the data everything looks nice so with that |
| 4:02:41 | we have now two dimensions |
| 4:02:47 | all right friends so with that we have covered a lot of stuff so we have |
| 4:02:50 | covered the customers and the products and we are left with only one table |
| 4:02:55 | where we have the transactions the sales and for the sales information we have |
| 4:02:59 | only data from the CRM we don't have anything from the Erp so let's go and |
| 4:03:03 | build it okay so now I have all those informations and now of course we have |
| 4:03:06 | only one table we don't have to do any Integrations and so on and now we have |
| 4:03:10 | to answer the big question do we have here a dimension or a fact well by |
| 4:03:14 | looking to those details we can see transactions we can see events we have a |
| 4:03:19 | lot of dates informations we have as well a lot of measures and metrics and |
| 4:03:23 | as well we have a lot of IDs so it is connecting multiple dimensions and this |
| 4:03:28 | is exactly a perfect setup for effects so we're going to go and use those |
| 4:03:32 | informations as effects and of course as we learned effect is connecting multiple |
| 4:03:37 | Dimensions we have to present in this fact the surrogate keys that comes from |
| 4:03:42 | the dimensions so those two informations the product key and the customer ID |
| 4:03:47 | those informations comes from the searce system and as we learned we want to |
| 4:03:50 | connect our data model using the surate keys so what we're going to do we're |
| 4:03:54 | going to replace those two informations with the surate keys that we have |
| 4:03:58 | generated and in order to do that we have to go and join now the two |
| 4:04:02 | dimensions in order to get the surate key and we call this process of course |
| 4:04:07 | data lookup so we are joining the tables in order only to get one information so |
| 4:04:12 | let's go and do that we will go with the lift joint of course not to lose any |
| 4:04:16 | transaction so first we're going to go and join it with the product key now of |
| 4:04:20 | course in the silver layer we don't have any ciruit Keys we have it in the good |
| 4:04:25 | layer so that means for the fact table we're going to be joining the server |
| 4:04:29 | layer together with the gold layer so gold dots and then the dimension |
| 4:04:34 | products and I'm going to just call it PR and we're going to join the SD using |
| 4:04:39 | the product key together with the product number |
| 4:04:43 | [Music] from the dimension and now the only |
| 4:04:46 | information that we need from the dimension is the key the sget key so |
| 4:04:51 | we're going to go over here and say product key and what I'm going to do I'm |
| 4:04:56 | going to go and remove this information from here because we don't need it we |
| 4:04:59 | don't need the original product key from The Source system we need the circuit |
| 4:05:03 | key that we have generated in our own in this data warehouse so the same thing |
| 4:05:07 | going to happen as well for the customer so gold Dimension customer again again |
| 4:05:13 | we are doing here a look up in order to get the information on SD so we are |
| 4:05:19 | joining using this ID over here equal to the customer ID because this is a |
| 4:05:26 | customer ID and what we're going to do the same thing we need the circuit key |
| 4:05:31 | the customer key and we're going to delete the ID because we don't need it |
| 4:05:35 | now we have the circuit key so now let's go and execute it and now with that we |
| 4:05:40 | have in our fact table the two keys from the dimensions and now this can help us |
| 4:05:45 | to connect the data model to connect the facts with the dimensions so this is |
| 4:05:49 | very necessary Step Building the fact table you have to put the surrogate keys |
| 4:05:53 | from the dimensions in the facts so that was actually the hardest part building |
| 4:05:57 | the facts now the next step all what you have to do is to go and give friendly |
| 4:06:01 | names so we're going to go over here and say order number then the surrogate keys |
| 4:06:06 | are already friendly so we're going to go over here and say this is the order |
| 4:06:10 | date and the next one going to be shipping |
| 4:06:14 | date and then the next one due date and the sales going to be I'm going to say |
| 4:06:21 | sales amount the |
| 4:06:24 | quantity and the final one is the price so now let's go and execute it and look |
| 4:06:30 | to the results so now as you can see the columns looks very friendly and now |
| 4:06:34 | about the order of the columns we use the following schema so first in the |
| 4:06:38 | fact table we have all the surrogate keys from the dimensions then second we |
| 4:06:42 | have all the dates and at the end you group up all the measures and the |
| 4:06:47 | matrics at the end of The Facts so that's it for the query for the facts |
| 4:06:51 | now we can go and build it so we're going to say create a view gold in the |
| 4:06:57 | gold layer and this time we're going to use the fact underscore and we're going |
| 4:07:01 | to go and call it sales and then don't forget about the ass so that's it let's |
| 4:07:05 | go and create it perfect now we can see the facts so with that we have three |
| 4:07:10 | objects in the gold layer we have two dimensions and one and facts and now of |
| 4:07:14 | course the next step with this we're going to go and check the quality of the |
| 4:07:18 | view so let's have a simple select fact sales so let's execute it |
| 4:07:25 | now by checking the result you can see it is exactly like the result from the |
| 4:07:29 | query and everything looks nice okay so now one more trick that I usually do |
| 4:07:33 | after building a fact is try to connect the whole data model in order to find |
| 4:07:38 | any issues so let's go and do that we will do just simple left join with the |
| 4:07:42 | dimensions so gold Dimension customers C and we will use the |
| 4:07:50 | [Music] keys and then we're going to say where |
| 4:07:54 | customer key is null so there is no matching so let's go and execute this |
| 4:07:59 | and with that as you can see in the results we are not getting anything that |
| 4:08:02 | means everything is matching perfectly and we can do as well the same thing |
| 4:08:07 | with the products so left join C them products p |
| 4:08:14 | on product key and then we connect it with the facts product key and then we |
| 4:08:20 | going to go and check the product key from the dimension like this so we are |
| 4:08:24 | checking whether we can connect the facts together with the dimension |
| 4:08:28 | products let's go and check and as you can see as well we are not getting |
| 4:08:31 | anything and this is all right so with that we have now SQL codes that is |
| 4:08:35 | tested and as well creating the gold layer now in The Next Step as you know |
| 4:08:40 | in our requirements we have to make clear documentations for the end users |
| 4:08:44 | in order to use our data model so let's go and draw a data model of the star |
| 4:08:52 | schema so let's go and draw our data model let's go and search for a table |
| 4:08:57 | and now what I'm going to do I'm going to go and take this one where I can say |
| 4:09:00 | what is the primary key and what is the for key and I'm going to go and change |
| 4:09:05 | little bit the design so it's going to be rounded and let's say I'm going to go |
| 4:09:08 | and change to this color and maybe go to the size make it 16 and then I'm going |
| 4:09:13 | to go and select all the columns and make it as well 16 just to increase the |
| 4:09:18 | size and then go to our range and we can go and increase it 39 so now let's go |
| 4:09:24 | and zoom in a little bit for the first table let's go and call it gold |
| 4:09:28 | Dimension customers and make it a little bit bigger like this and now we're going |
| 4:09:33 | to go and Define here the primary key it is the customer key and what else we're |
| 4:09:37 | going to do we're going to go and list all the columns in the dimension is |
| 4:09:40 | little bit annoying but the results going to be awesome so what do we we |
| 4:09:43 | have the customer ID we have the customer number and then we have the |
| 4:09:49 | first name now in case you want a new rows so you can hold control and enter |
| 4:09:55 | and you can go and add the other columns so now pause the video and then go and |
| 4:09:59 | create the two Dimensions the customers and the products and add all the columns |
| 4:10:03 | that you have built in the [Music] |
| 4:10:08 | view welcome back so now I have those two Dimensions the third one one going |
| 4:10:13 | to be the fact table now for the fact table I'm going to go with different |
| 4:10:17 | color for example the blue and I'm going to go and put it in the middle something |
| 4:10:21 | like this so we're going to say gold fact sales and here for that we don't |
| 4:10:27 | have primary key so we're going to go and delete it and I have to go and add |
| 4:10:31 | all The Columns of the facts so order number products key customer key okay |
| 4:10:37 | all right perfect now what we can do we can go and add the foreign key |
| 4:10:41 | information so the product key is a foreign key key for the products so |
| 4:10:44 | you're going to say fk1 and the customer key going to be the foreign key for the |
| 4:10:48 | customers so fk2 and of course you can go and increase the spacing for that |
| 4:10:53 | okay so now after we have the tables the next step in data modeling is to go and |
| 4:10:57 | describe the relationship between these tables this is of course very important |
| 4:11:00 | for reporting and analytics in order to understand how I'm going to go and use |
| 4:11:05 | the data model and we have different types of relationships we have one to |
| 4:11:08 | one one too many and in Star schema data model the relationship between the |
| 4:11:12 | dimension and the fact is one too many and that's because in the table |
| 4:11:16 | customers we have for a specific customer only one record describing the |
| 4:11:20 | customer but in the fact table the customer might exist in multiple records |
| 4:11:25 | and that's because customers can order multiple times so that's why in fact it |
| 4:11:29 | is many and in the dimension side it is one now in order to see all those |
| 4:11:33 | relationships we're going to go to the menu to the left side and as you can see |
| 4:11:37 | we have here entity relations and now you have different types of arrows so |
| 4:11:41 | here for example we have zero to many one one to many one to one and many |
| 4:11:45 | different types of relations so now which one we going to take we're going |
| 4:11:49 | to go and pick with this one so it says one mandatory so that means the customer |
| 4:11:53 | must exist in the dimension table too many but it is optional so here we have |
| 4:11:57 | three scenarios the customer didn't order anything or the customer did order |
| 4:12:01 | only once or the customer did order many things so that's why in the fact table |
| 4:12:06 | it is optional so we're going to take this one and place it over here so we're |
| 4:12:10 | going to go and connect this part to the customer Dimension and the many parts to |
| 4:12:16 | the facts well actually we have to do it on the customers so with that we are |
| 4:12:21 | describing the relationship between the dimensions and fact with one to many one |
| 4:12:25 | is mandatory for the customer Dimension and many is optional to the facts so we |
| 4:12:30 | have the same story as well for the products so the many part to the facts |
| 4:12:35 | and the one goes to the products so it's going to look like this each time you |
| 4:12:39 | are connecting new dimension to the fact table it is usually one too many |
| 4:12:44 | relationship so you can go and add anything you want to this model like for |
| 4:12:47 | example a text like explaining something for example if you have some complicated |
| 4:12:52 | calculations and so on you can go and write this information over here so for |
| 4:12:56 | example we can say over here sales calculation we can make it a little bit |
| 4:13:00 | smaller so let's go with 18 so we can go and write here the formula for that so |
| 4:13:06 | sales equal quantity multipli with a price and make this a little bit bigger |
| 4:13:13 | so it is really nice info that we can add it to the data model and even we can |
| 4:13:17 | go and Link it to the column so we can go and take this arrow for example with |
| 4:13:22 | it like this and Link it to the column and with that you have as well nice |
| 4:13:26 | explanation about the business rule or the calculation so you can go and add |
| 4:13:30 | any descriptions that you want to the data model just to make it clear for |
| 4:13:34 | anyone that is using your data model so with that you don't have only like three |
| 4:13:38 | tables in the database you have as well like some kind of documentations and |
| 4:13:42 | explanation in one Blick we can see how the data model is built and how you can |
| 4:13:47 | connect the tables together it is amazing really for all users of your |
| 4:13:50 | data model all right so now with that we have really nice data model and now in |
| 4:13:55 | The Next Step we're going to go and create quickly a data |
| 4:14:01 | catalog all right great so with that we have a data model and we can say we have |
| 4:14:05 | something called a data products and we will be sharing this data product with |
| 4:14:10 | different type of users and there's something that's every every data |
| 4:14:13 | product absolutely needs and that is the data catalog it is a document that can |
| 4:14:18 | describe everything about your data model The Columns the tables maybe the |
| 4:14:23 | relationship between the tables as well and with that you make your data product |
| 4:14:26 | clear for everyone and it's going to be for them way easier to derive more |
| 4:14:31 | insights and reports from your data product and what is the most important |
| 4:14:34 | one it is timesaving because if you don't do that what can happen each |
| 4:14:39 | consumer each user of your data product will keep asking you the same question |
| 4:14:43 | questions about what do you mean with this column what is this table how to |
| 4:14:46 | connect the table a with the table B and you will keep repeating yourself and |
| 4:14:50 | explaining stuff so instead of that you prepare a data catalog a data model and |
| 4:14:55 | you deliver everything together to the users and with that you are saving a lot |
| 4:14:59 | of time and stress I know it is annoying to create a data catalog but it is |
| 4:15:03 | Investments and best practices so now let's go and create one okay so now in |
| 4:15:07 | order to do that I've have created a new file called Data catalog in the folder |
| 4:15:11 | documents and here what we're going to do is very St straightforwards we're |
| 4:15:13 | going to make a section for each table in the gold layer so for example we have |
| 4:15:17 | here the table dimension customers what you have to do first is to describe this |
| 4:15:21 | table so we are saying it stores details about the customers with the |
| 4:15:25 | demographics and Geographics data so you give a short description for the table |
| 4:15:29 | and then after that you're going to go and list all your columns inside this |
| 4:15:33 | table and maybe as well the data type but what is way important is the |
| 4:15:36 | description for each column so you give a very short description like for |
| 4:15:40 | example here the gender of the customer now one of the best practices of |
| 4:15:44 | describing a column is to give examples because you can understand quickly the |
| 4:15:49 | purpose of the columns by just seeing an example right so here we are seeing we |
| 4:15:52 | can find inside it a male female and not available so with that the consumer of |
| 4:15:56 | your table can immediately understand uhhuh it will not be an M or an F it's |
| 4:16:01 | going to be a full friendly value without having them to go and query the |
| 4:16:04 | content of the table they can understand quickly the purpose of the column so |
| 4:16:08 | with that we have a full description for all the columns of our Dimension the |
| 4:16:12 | same thing we're going to do for the products so again a description for the |
| 4:16:15 | table and as well a description for each column and the same thing for the facts |
| 4:16:20 | so that's it with that you have like data catalog for your data product at |
| 4:16:24 | the code layer and with that the business user or the data analyst have |
| 4:16:28 | better and clear understanding of the content of your gold layer all right my |
| 4:16:32 | friends so that's all for the data catalog in The Next Step we're going to |
| 4:16:35 | go back to Dro where we're going to finalize the data flow diagram so let's |
| 4:16:40 | go |
| 4:16:44 | okay so now we're going to go and extend our data flow diagram but this time for |
| 4:16:48 | the gold layer so now let's go and copy the whole thing from the silver layer |
| 4:16:52 | and put it over here side by side and of course we're going to go and change the |
| 4:16:56 | coloring to the gold and now we're going to go and rename stuff so this is the |
| 4:17:02 | gold layer but now of course we cannot leave those tables like this we have |
| 4:17:06 | completely new data model so what do we have over here we have the fact sales we |
| 4:17:11 | have dimension customers and as well we have Dimension products so now what I'm |
| 4:17:18 | going to do I'm going to go and remove all those stuff we have only three |
| 4:17:21 | tables and let's go and put those three tables somewhere here in the center so |
| 4:17:25 | now what you have to do is to go and start connecting those stuff I'm going |
| 4:17:28 | to go with this Arrow over here direct connection and start connecting stuff so |
| 4:17:34 | the sales details goes to the fact table maybe put the fact table over here and |
| 4:17:38 | then we have the dimension customer this comes from the CRM customer our info and |
| 4:17:43 | we have two tables from the Erp it comes from this table as well and the location |
| 4:17:49 | from the Erp now the same thing goes for the products it comes from the product |
| 4:17:55 | info and comes from the categories from the Erp now as you can see here we have |
| 4:18:00 | cross arrows so what we going to do we can go and select everything and we can |
| 4:18:03 | say line jumps with a gap and this makes it a little bit like Pitter individual |
| 4:18:08 | for the arrows so now for example if someone asks you where the data come |
| 4:18:12 | from for the dimension products you can open this diagram and tell them okay |
| 4:18:16 | this comes from the silver layer we have like two tables the product info from |
| 4:18:21 | the CRM and as well the categories from the Erp and those server tables comes |
| 4:18:25 | from the pron layer and you can see the product info comes from the CRM and the |
| 4:18:30 | category comes from the Erp so it is very simple we have just created a full |
| 4:18:34 | data lineage for our data warehouse from the sources into the different layers in |
| 4:18:38 | our data warehouse and data lineage is is really amazing documentation that's |
| 4:18:42 | going help not only your users but as well the developers all right so with |
| 4:18:46 | that we have very nice data flow diagram and a data lineage all right so we have |
| 4:18:50 | completed the data flow it's really feel like progress like achievement as we are |
| 4:18:54 | clicking through all those tasks and now we come to the last task in building the |
| 4:18:58 | data warehouse where we're going to go and commit our work in the get |
| 4:19:05 | repo okay so now let's put our scripts in the project so we're going to go to |
| 4:19:09 | the scripts over here we have here bronze silver but we don't have a gold |
| 4:19:12 | so let's go and create a new file we're going to have gold/ and then we're going |
| 4:19:16 | to say ddl gold. SQL so now we're going to go and paste our views so we have |
| 4:19:22 | here our three views and as usual at the start we going to describe the purpose |
| 4:19:26 | of the views so we are saying create gold views this script can go and create |
| 4:19:30 | views for the code layer and the code layer represent the final Dimension and |
| 4:19:34 | fact tables the star schema each view perform Transformations and combination |
| 4:19:38 | data from the server layer to produce business ready data sets and those us |
| 4:19:42 | can be used for analytics and Reporting so that it let's go and commit it okay |
| 4:19:47 | so with that as you can see we have the PRS the silver so we have all our etls |
| 4:19:53 | and scripts in the reposter and now as well for the gold layer we're going to |
| 4:19:57 | go and add all those quality checks that we have used in order to validate the |
| 4:20:01 | dimensions and facts so we're going to go to The Taste over here and we're |
| 4:20:05 | going to go and create a new file it's going to be quality checks gold and the |
| 4:20:10 | file type is SQL so now let's go and paste our quality checks so we have the |
| 4:20:14 | check for the fact the two dimensions and as well an explanation about the |
| 4:20:19 | script so we are validating the integrity and the accuracy of the gold |
| 4:20:22 | layer and here we are checking the uniqueness of the circuit keys and |
| 4:20:25 | whether we are able to connect the data model so let's put that as well in our |
| 4:20:29 | git and commit the changes and in case we come up with a new quality checks |
| 4:20:34 | we're going to go and add it to our script here so those checks are really |
| 4:20:37 | important if you are modifying the atls or you want to make sure that after each |
| 4:20:41 | ATL those script SC should run and so on it is like a quality gate to make sure |
| 4:20:46 | that everything is fine in the gold layer perfect so now we have our code in |
| 4:20:50 | our repo story okay friends so now what you have to do is to go and finalize the |
| 4:20:54 | get repo so for example all the documentations that we have created |
| 4:20:58 | during the projects we can go and upload them in the docs so for example you can |
| 4:21:02 | see here the data architecture the data flow data integration data model and so |
| 4:21:06 | on so with that each time you edit those pages you can commit your work and you |
| 4:21:10 | have likey version of that and another thing that you can do is that you go to |
| 4:21:15 | the read me like for example over here I have added the project overview some |
| 4:21:19 | important links and as well the data architecture and a little description of |
| 4:21:23 | the architecture of course and of course don't forget to add few words about |
| 4:21:27 | yourself and important profiles in the different social medias all right my |
| 4:21:31 | friends so with that we have completed our work and as well closed the last |
| 4:21:35 | epek building the gold layer and with that we have completed all the faces of |
| 4:21:40 | building a data warehouse everything is 100% And this feels really nice all |
| 4:21:45 | right my friends so if you're still here and you have built with me the data |
| 4:21:49 | warehouse then I can say I'm really proud of you you have built something |
| 4:21:53 | really complex and amazing because building a data warehouse is usually a |
| 4:21:57 | very complex data projects and with that you have not only learned SQL but you |
| 4:22:01 | have learned as well how we do a complex data projects in real world so with that |
| 4:22:06 | you have a real knowledge and as well amazing portfolio that you can share |
| 4:22:10 | with others if you are applying for a job or if you are showcase that you have |
| 4:22:14 | learned something new and with that you have experienced different rules in the |
| 4:22:17 | project what the data Architects and the data Engineers do in complex data |
| 4:22:21 | projects so that was really an amazing journey even for me as I'm creating this |
| 4:22:25 | project so now in the next and with that you have done the first type of data |
| 4:22:29 | analytics projects using SQL the data warehousing now in The Next Step we're |
| 4:22:33 | going to do another type of projects the exploratory data analyzes Eda where |
| 4:22:37 | we're going to understand and explore our data sets if you like this video and |
| 4:22:41 | you want me to create more content like this I'm going to really appreciate it |
| 4:22:45 | if you support the channel by subscribing liking sharing commenting |
| 4:22:50 | all those stuff going to help the Channel with the YouTube algorithm and |
| 4:22:53 | as well my content going to reach to the others so thank you so much for watching |
| 4:22:58 | and I will see you in the next tutorial bye |
remove only Vietnamese
