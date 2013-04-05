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

`;=` : **Key reference** :: _Required_

Format: `;=<key character>:<GameObject path>`

ex: `;=T:Ground` means that the `T` character should create duplicates of the `Ground` GameObject in the hierarchy.

---

`;n=` : **Parent container name** :: _Optional_

Format: `;n=<string>`

If supplied, all imported instances will be grouped together under a single GameObject with the specified name.

This option can also be set individual instance containers.

ex: `;=?:QuestionBlock,n=Blocks` means that the parent for all `QuestionBlock` instances will be named `Blocks` instead of the default `QuestionBlockContainer`.

Multiple `GameObjects` can be assigned to the same parent container.

---

`;z=` : **Global z-depth** :: _Optional_

Format: `;z=<integer>`

If set, all instance containers will be offset in the z-direction by this amount.

This option can also be set individual instance containers.

ex: `;=T:Ground,z=10` means the `GroundContainer` GameObject will have it's z transform set to 10.

---

`;s=` : **Scale** :: _Optional_

Format: `;s=<integer>`

ex: `;s16` means that 1 grid square in the Text Gen file equals 16 units in unity.

---

`;+` : **Start map definition** :: _Required_

This should always be the last configuration option in your file. It means that all of the lines after this one until we reach the end of the file define the level.

---

**Notes:**

The back tick (\`) is a special character that is ignored in the map definition. It's useful for visually filling out parts of your map definition file.
In the example below, the `Pipe` GameObject is actually 2x2 squares in size. Using the back tick to visually fill out the rest of the pipe helps show how much space it takes up.


Example Text Gen file
----------------------

```
;n=LevelContainer
;s=16
;z=-10
;=@:MarioSprite,n=Characters
;=G:GoombaSprite,n=Characters
;=T:Ground,z=10
;=?:QuestionBlock,n=Blocks
;==:Brick,z=0,n=Bricks
;=P:Pipe
;+

          ?


    ?   =?=?=
               ``
 @        G    P`
TTTTTTTTTTTTTTTTTTT

```


Usage Instructions
------------------

1. Prepare your prefab instances in the Hierarchy.
2. Tag each of the prefab instances you want to use as a template with `TextGenTemplate`.
3. Go to `GameObject > Import From TextGen File...`.
4. Select the Text Gen file you want to import from your project Assets.
5. Click the `Import!` button.
