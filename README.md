Text Gen
========

Generate 2D levels in Unity 3D from a text file.

Works in conjunction with Kindred Sprite.
* https://github.com/whtt-eric/kindred-sprite

Installation
------------

Download the `Editor` folder to `Assets/Plugins/TextGen`.


Configuration Options
---------------------

Configuration lines always start with a semicolon (`;`).

`;=` : **Key reference**

Format: `<key character>:<GameObject path>`

ex: `;=T:Ground` means that the `T` character should create duplicates of the `Ground` GameObject in the hierarchy.

`;s` : **Scale**

Format: `<integer>`

ex: `;s16` means that 1 grid square in the Text Gen file equals 16 units in unity.

`;+` : **Start map definition**

This should always be the last configuration option in your file. It means that all of the lines after this one until we reach the end of the file define the level.


Example Text Gen file
----------------------

```
;=@:MarioSprite
;=T:Ground
;=?:QuestionBlock
;==:Brick
;s16
;+

          ?


    ?   =?=?=

 @
TTTTTTTTTTTTT

```


Usage Instructions
------------------

For each key reference you define in your Text Gen file, there must be one, and **only one** instance of the GameObject in the hierarchy.

1. Go to `File > Import TextGen File...`.
2. Select the Text Gen file you want to import from your project Assets.
3. Click the `Import!` button.


TODO
----

* Add `;n<string>` option to group all instances under a single GameObject
* Group all instances of one GameObject together in a parent GameObject (ex: `GroundContainer`)
* Add `;z<int>` option to set the z-depth of the GameObjects
* Allow setting of z-depth on individual reference definitions. Ex: `;=T:Ground,z10`
* Allow defining of multiple maps per file. This would be helpful if you wanted to define your foreground and background spirtes separately (maybe because there's some overlap?).
