# Kotlin

## CRUD (DAO)

### Create (C)

**Insert a single game**:
```
@Insert
suspend fun insertGame(game: Game)
```

**Insert multiple games**:
```
@Insert
suspend fun insert(game: List<Game>)
```
### Read (R)

**Retrieve all games ordered by release date**:
```
@Query("SELECT * from game ORDER BY `release` ASC")
fun getGames(): LiveData<List<Game>>
```
### Update (U)

Your DAO currently does not have an update method. You can add one like this:
```
@Query("UPDATE game SET title = :title, `release` = :release WHERE id = :id")
suspend fun updateGame(id: Int, title: String, release: String)
```

Or for updating the entire `Game` object:
```
@Update
suspend fun updateGame(game: Game)
```
### Delete (D)

**Delete a specific game**:

```
@Delete
suspend fun delete(game: Game)
```

**Delete all games**:

```
@Query("DELETE from game")
suspend fun deleteAll()
```