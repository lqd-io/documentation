
If you use more than a variable for a Target (defined on Liquid dashboard), all variables affected by that target become dependant on each others.

This means that, if a variable value is fallen back, all the other variables on the same Target will be also fallen back.

Situations like these will only occur if you do something really wrong in your variable settings (e.g. data type mismatch between code and Liquid dashboard), but this mechanism will ensure consistency in your app.
