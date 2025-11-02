<h1 align="center">NoteKeeperApp<h1>

---

## Short Reflection:
### 1. How did you implement CRUD using SQLite?
> I implemented CRUD (Create, Read, Update, Delete) by creating a dedicated helper class called NotesDatabaseHelper, which extends SQLiteOpenHelper. This class manages all database interactions:
> * Create: I made an addNote() method and then uses the db.insert() command to add the data as a new row in the notes table
> * Read: I made a getAllNotes() method. It runs a db.rawQuery("SELECT * FROM notes") to get all rows. It then loops through the resulting Cursor, converts each row into a Note object, and returns the complete List<Note>
> * Update: The updateNote() method takes an existing Note object. It uses ContentValues to package the new title and content, and then calls db.update() with a WHERE clause ("$COLUMN_ID = ?"), so it only updates the specific row that matches the note's ID
> * Delete: The deleteNote() method takes a noteId. It uses db.delete() with a WHERE clause to find and remove that specific row from the table

### 2. What challenges did you face in maintaining data persistence?
> * The main challenge was that the note list wouldn't refresh after adding or editing a note. I fixed this by forcing the list to reload its data from the database in the onResume() method, so it always shows the latest data when the user returns to the main screen

### 3. How could you improve performance or UI design in future versions?
> * Empty State: When no notes exist, the screen is just blank. I would add a message in the middle of the screen that says "No notes yet. Tap the '+' to add one!"
> * Search/Filter: I could add a search bar to the MainActivity to allow the user to filter their notes by title or content
> * Better Delete: Instead of a long-press, I could add a "swipe-to-delete" gesture on the RecyclerView items, which is a more common and discoverable pattern in mobile apps
