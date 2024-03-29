Instructions to run the application

STEP 1: Set up SQL on GCP (This was done in class.  If you missed it, follow
        the instructions in the handout GCP SQL setup instruction posted on the 
        course site: 
        https://docs.google.com/document/d/1X7vnexMHT8upAUNUj-xtlwQJIMp63CZ-PAEtYBv1YHI/edit?usp=sharing

STEP 2: If you haven't yet created a database named population, go to the SQL
        interface on GCP and create the database.  This is the last step in the
        handout linked in Step 1.

STEP 3: Install the python DB related python modules from the command line:
sudo pip3 install requests flask-mysql flask-wtf flask-sqlalchemy mysql-connector-python

STEP 4: Go to the project home directory, edit .flaskenv and replace
the asterisks in the following:

      MYSQL_IP='**********'   # IP address of your SQL instance on GCP
      MYSQL_PASS='********'   # root password of your SQL instance

    Save your edits and quit micro.

STEP 5:
  *********
  This step is only needed the first time you run the application in order
  to create the table (or to delete the table and start fresh).
  *********
    Still from the project directory, perform the following:
    - Start the flask shell by typing:     flask shell
    - At the prompt (>>>), run following Python statement in
      sequence:
            from app import app, db
            db.create_all()
            quit()    # this takes you back to the terminal prompt

   The create_all function creates the database schema defined in app/models.py.
   In MySQL Workbench, connect to your database on GCP and refresh your Schemas.
   You should see the table cities under population.

   **** To delete the data and recreate the table *****
  Start the flask shell (flask shell) and then type:
  			from app import app, db 
  			db.drop_all() 
  			db.create_all()

STEP 6: Now run the Flask application from the project top-level directory:

    flask run
