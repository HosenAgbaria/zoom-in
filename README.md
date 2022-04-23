# zoom-in
Zoom clone


    CREATE TABLE referees (
    referee_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) ,
    last_name VARCHAR(50) ,
    birth_date date default current_date,
    nationality VARCHAR(50) 
    );

    CREATE TABLE coaches (
    coach_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) ,
    last_name VARCHAR(50) ,
    birth_date date default current_date,
    nationality VARCHAR(50)
    );

    CREATE TABLE teams(
    team_id SERIAL PRIMARY KEY,
    team_name VARCHAR(50) ,
    coach_name VARCHAR(10) ,
    establishment_date date default current_date,
    coach_id integer REFERENCES coaches(coach_id),
    league_name varchar(50),
    staduim_name varchar(50),
    country varchar(50)
    );

    CREATE TABLE players(
    player_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) ,
    last_name VARCHAR(50) ,
    birth_date date default current_date,
    nationality VARCHAR(50) ,
    team_id integer REFERENCES teams(team_id),
    postion VARCHAR(50) 
    );


    CREATE TABLE games(
    game_id SERIAL PRIMARY KEY,
    home_team_id integer REFERENCES teams(team_id),
    away_team_id integer REFERENCES teams(team_id),
    refere_id integer REFERENCES referees(refere_id),
    final_result VARCHAR(50) ,
    winner VARCHAR(50) ,
    game_date date default current_date,
    staduim_name varchar(50) 
    );

    CREATE TABLE goals(
    goal_id SERIAL PRIMARY KEY,
    player_id integer REFERENCES players(player_id),
    minute VARCHAR(50) ,
    staduim_name varchar(50) ,
    team_id integer REFERENCES teams(team_id),
    game_id integer REFERENCES games(game_id),
    own_goal BOOLEAN default false,
    );



    -- 


    INSERT INTO referees (first_name,last_name,birth_date,nationality)
    VALUES
    ('Pep ','Guardiola ','Jun 9, 1990','spain'),
    ('Massimiliano ','Allegri ','May 4, 1983','Italy'),
    ('Antonio ','Conte ','Jan 1, 1999','Italy'),
    ('Jupp ','Heynckes ','Jan 19, 1963','Netherlands'),
    ('Dante','Barker','Dec 29, 1986','Vietnam'),
    ('Blaze','Albert','Jan 18, 1990','Turkey'),
    ('Kaseem','Morse','Apr 14, 1986','Singapore'),
    ('Hiram','Perez','Apr 12, 1993','Colombia'),
    ('Duncan','Moody','Feb 2, 1982','South Korea'),



    CREATE TABLE games(
    home_team_id integer REFERENCES teams(team_id),
    away_team_id integer REFERENCES teams(team_id),
    refere_id integer REFERENCES referees(refere_id),
    final_result VARCHAR(50) ,
    winner_team_id integer REFERENCES teams(team_id),
    game_date date default current_date,
    staduim_name varchar(50) 
    );



    INSERT INTO games (game_date,home_team_id,away_team_id,final_result,refere_id,winner_team_id,staduim_name)
    VALUES
    ('Jul 26, 2021',4,3,'1-0',1,3,'BRIDGE'),
    ('Nov 30, 2021',1,2,'3-5',7,2,'STADIUM'),
    ('May 10, 2021',2,1,'3-2',1,1,'CAMP NOU'),
    ('May 9, 2021',1,6,'2-3',1,6,'STAMFORD'),
    ('Jun 1, 2022',5,3,'1-0',5,5,'STADIUM'),
    ('Jul 13, 2022',3,1,'1-0',5,3,'STADIO'),
    ('Nov 8, 2022',6,3,'4-5',2,6,'CAMP NOU'),
    ('Jul 27, 2021',4,1,'4-3',1,4,'STADIO'),
    ('Sep 5, 2022',5,4,'3-1',2,5,'BERNABÉU'),
    ('Mar 3, 2023',4,3,'1-0',6,3,'CAMP NOU');


    INSERT INTO teams (team_name,establishment_date,coach_id,league_name,staduim_name,country)
    VALUES
    ('ARSENAL','Apr 29, 1886',6,'PREMIER LEAGUE','EMIRATES STADIUM ','ENGLAND'),
    ('Chelsea','Dec 1, 1905',5,'PREMIER LEAGUE','STAMFORD BRIDGE ','ENGLAND'),
    ('Liverpool','Oct 9, 1892',4,'PREMIER LEAGUE',' ANFIELD ','ENGLAND'),
    ('Real Madrid','Jul 3, 1902',5,'LA LIGA','SANTIAGO BERNABÉU ','SPAIN'),
    ('Barcelona','Dec 10, 1899',9,'LA LIGA',' CAMP NOU ','SPAIN'),
    ('AC Milan','Jan 4, 1899',2,' SERIE A','SAN SIRO','ITALY'),
    ('AS Roma','Mar 26, 1927',6,'SERIE A',' STADIO OLIMPICO ','ITALY'),
    ('Juventus','Jan 18, 1897',5,'SERIE A','JUVENTUS STADIUM ','ITALY'),



    INSERT INTO coaches (first_name,last_name,birth_date,nationality)
    VALUES
    ('Kasimir','Doyle','Aug 30, 1996','Italy'),
    ('Rashad','Mendez','May 2, 1986','Sweden'),
    ('Noah','Morse','Mar 19, 1991','Germany'),
    ('Aidan','Avila','Mar 6, 1992','Pakistan'),
    ('Kuame','Walker','Aug 12, 1996','Ireland'),
    ('Bevis','Horne','Nov 5, 1978','Brazil'),
    ('Giacomo','Petty','Jun 14, 1995','Spain'),
    ('Honorato','Langley','Jan 5, 1993','Vietnam'),
    ('Sean','Ashley','Aug 3, 1977','Philippines'),
    ('Orlando','Green','Dec 20, 1987','Austria');


    INSERT INTO players (first_name,last_name,birth_date,nationality,team_id,postion)
    VALUES
    ('Martin','Robles','May 17, 1988','United States',3,'Center'),
    ('Orson','Blair','Dec 22, 1990','Chile',5,'Goalkeeper'),
    ('Mason','Andrews','Mar 13, 1991','Poland',3,'Goalkeeper'),
    ('Gannon','Montoya','Jan 20, 1991','United States',3,'Center'),
    ('Lars','Dejesus','Apr 17, 1992','New Zealand',3,'Tackle'),
    ('Brian','Cain','Apr 22, 1977','Ireland',1,'Center'),
    ('Chase','Cook','Jan 29, 1989','Norway',6,'Guard'),
    ('Hyatt','Fischer','Sep 21, 1986','Chile',1,'Goalkeeper'),
    ('Ira','Arnold','Mar 22, 1984','Brazil',6,'Guard'),
    ('Gabriel','Vincent','Nov 9, 1988','Russian Federation',3,'Center');
    INSERT INTO players (first_name,last_name,birth_date,nationality,team_id,postion)
    VALUES
    ('Harding','Marks','Jul 24, 1981','South Africa',6,'Goalkeeper'),
    ('Asher','May','Aug 7, 1979','Ukraine',6,'Center'),
    ('Len','Osborn','Jul 6, 1980','Chile',2,'Tackle'),
    ('Macon','Colon','Feb 10, 1982','Italy',4,'Center'),
    ('Nathan','Cooke','Aug 4, 1988','United Kingdom',5,'Goalkeeper'),
    ('Eric','Blevins','Aug 13, 1981','Nigeria',3,'Tackle'),
    ('Jeremy','Willis','Aug 17, 1976','Turkey',4,'Guard'),
    ('Micah','Haley','Aug 9, 1997','Canada',7,'Guard'),
    ('Colby','Gilbert','Apr 21, 1985','Nigeria',2,'Guard'),
    ('Adrian','Stevens','Jun 30, 1979','Poland',1,'Guard');



