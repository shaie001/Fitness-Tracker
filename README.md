Fitness Tracker
Description
Track your workouts with Fitness Tracker. The app will keep track of every exercise in your workout. The app dashboard will display weekly summary graphs of all workouts done in a week.

Table of Contents
Installation
Usage
Screenshots
Snippets
Credits
License
Installation
Clone repository.
Check in routes/api-routes and comment in block of code if you want the database to be prepopulated with dummy values
npm install
node server.js
Running seeders/seed.js is optional to have a prepopulated database.

Live Site

Usage
Screeshots
Homepage displaying last workout
Site

Creating Workouts
Site

Last Week's Summary
Site

Snippets
Adding to an array type
    // add exercise
    app.put("/api/workouts/:id", (req, res) => {

        db.Workout.findOneAndUpdate(
            { _id: req.params.id },
            {
                $inc: { totalDuration: req.body.duration },
                $push: { exercises: req.body }
            },
            { new: true }).then(dbWorkout => {
                res.json(dbWorkout);
            }).catch(err => {
                res.json(err);
            });

    });
    
This function will add an exercise to the array of exercises that belong to the workout with the given id. Here we will locate the workout with the given ID and update its fields. We will increase the total duration of the workout by the duration of the exercise being inserted. We will push the exercise to the array of exercises.
