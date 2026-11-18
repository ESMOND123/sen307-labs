# VUA-SEN307 Lab 4: Referential Integrity Notes

**Name:** Esmond Oise-amu  
**Matric Number:** Vug/Sen/24/11201  
**Course:** VUA-SEN307 Database Systems  

In Part 4, attempting to delete `Library and Information Science` from the `Department` table produced **Error 1451: Cannot delete or update a parent row: a foreign key constraint fails**[cite: 16]. MySQL blocked the deletion because a child record (`Transfer Student`, matric `20239999`) in the `Student` table still referenced that department's `dept_id`, and removing the parent record would break referential integrity[cite: 15, 16]. I fixed this properly by executing an `UPDATE` statement to reassign `Transfer Student` to the `Software Engineering` department before deleting `Library and Information Science` from `Department`[cite: 16]. Alternatively, the foreign key on `Student` could have been configured with `ON DELETE CASCADE` (to automatically remove dependent child records) or `ON DELETE SET NULL` (to nullify `dept_id` when the parent department is deleted).