package com.mynotes.notesappmvvmkotlin.Database

import android.content.Context
import androidx.room.Room
import androidx.room.RoomDatabase
import com.mynotes.notesappmvvmkotlin.Dao.NotesDao

abstract class NotesDatabase : Roomdatabase() {

     abstract fun myNotesDao(): NotesDao

     companion object {
         @volatile
         var INSTANCE: NotesDatabase? = null

         fun getDatabaseInstance(context.Context): NotesDatabase {

             val tempInstnce = INSTANCE
             if (tempInstance != null) {
                 return tempInstnce
             }
             synchronized(this)
             {
                   val roomDatabaseInstance =
                       Room.databaseBuilder(context, NotesDatabase::class.java, name"Notes").build()
                   INSTANCE = roomDatabaseInstance
                   return return roomDatabaseInstance
             }
         }
     }
 }
