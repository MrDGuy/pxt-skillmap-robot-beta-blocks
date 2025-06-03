# Customized Tilemaps

## Introduction @unplugged

You will now demonstrate all that you have learned about the robot and tilemaps.

## Step One

Create two custom tilemaps that each contain a startTile and one with a connection tile and the other with a goalTile.  Make sure you create a custom coinTile to place coins on your tilemaps.  Name the first tilemap level1 and the second level2. 

Here is a slideshow showing you how to create custom tilemaps that have a connection tile named door1.
https://docs.google.com/presentation/d/197ps_WnRzQuTZUjZKKPDIfWs46FLAPVblv8GIuTB6w8/edit?usp=sharing

## Step One

Use the ``||tiles:tilemap ||`` code to create a new tilemap. Click the map and then Create a custom tilemaps that contains a startTile and a connection tile named door1.  Make sure you create a custom coinTile to place coins on your tilemaps.  Name the first tilemap level1.

```blocks
tiles.createMap(tilemap`level1`)
```

## Step Two

After that in the front of the line of code write tile_map1 =.

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
```

## Step Three

Use the ``||tiles:tilemap ||`` code to create a new tilemap. Click the map and then Create a custom tilemaps that contains a startTile and a goalTile.  Make sure you create a custom coinTile to place coins on your tilemaps.  Name the second tilemap level2.

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
tiles.createMap(tilemap`level2`)
```

## Step Four

After that in the front of the line of code write tile_map2 =.
![Customize your tilemap](https://raw.githubusercontent.com/MrDGuy/pxt-skillmap-robot/main/docs/static/variables-tilemaps-1.png "Customize Tilemap" )

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
```

## Step Five @unplugged

Load the tilemap tile_map1. Code: tiles.load_map(tile_map1)
![Customize your tilemap](https://raw.githubusercontent.com/MrDGuy/pxt-skillmap-robot/main/docs/static/variables-tilemaps-2.gif "Customize Tilemap" )

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
```

## Step Six

Use the ``||robot:begin screen ||`` code to start your robot on the start tile and set up the tilemap.

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
robot.beginScreen()
```

## Step Seven

Connect the two tilemaps with ``||tiles:connect tilemap1 and tilemap2 by connection ||`` code.  

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
robot.beginScreen()
tiles.connectMapById(tileMap1, tileMap2, ConnectionKind.Door1)
```

## Step Eight
Change tiles.connect_map_by_id(tilemap1, tilemap2, ConnectionKind.door1) to tiles.connect_map_by_id(tile_map1, tile_map2, ConnectionKind.door1)

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
robot.beginScreen()
tiles.connectMapById(tileMap1, tileMap2, ConnectionKind.Door1)
```

## Step Eight

Pull in the code from the ``||scene:run code on sprite of kind overlaps tile at location||`` in the ``||scene:scene||`` category under the tilemaps section.

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
robot.beginScreen()
tiles.connectMapById(tileMap1, tileMap2, ConnectionKind.Door1)

scene.onOverlapTile(SpriteKind.Player, img` `, function(sprite: Sprite, location: tiles.Location) {
    
})
```

## Step Nine

Replace the img(""" """) code at the end of the overlap tile code with assets.tile("""door1""")

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
robot.beginScreen()
tiles.connectMapById(tileMap1, tileMap2, ConnectionKind.Door1)

scene.onOverlapTile(SpriteKind.Player, assets.tile`door1`, function(sprite: Sprite, location: tiles.Location) {
    
})
```

## Step Ten

Replace the pass in the on_overlap_tile function with ``||tiles:set current tilemap to map||`` code to load tile_map2. Also, include a new ``||robot:begin screen||`` to load the next level properly.

```blocks
let tileMap1 = tiles.createMap(tilemap`level1`)
let tileMap2 = tiles.createMap(tilemap`level2`)
tiles.loadMap(tileMap1)
robot.beginScreen()
tiles.connectMapById(tileMap1, tileMap2, ConnectionKind.Door1)

scene.onOverlapTile(SpriteKind.Player, assets.tile`door1`, function(sprite: Sprite, location: tiles.Location) {
    tiles.loadMap(tileMap2)
    robot.beginScreen()
})
```

## Step Twelve

Use the ``||robot:move forward||`` code to move the robot. Change the direction the robot is facing with the ``||robot:turn right||`` and ``||robot:turn left||`` code.  Also, use the ``||robot:collect coin||`` to collect all the coins along the way. Move the robot to the goal tile.

```blocks
robot.moveForward()
robot.turnRight()
robot.turnLeft()
robot.collectCoin()
```


```customts
    game.onUpdate(function () {
        if (robot.goalReached()) {
            music.play(music.melodyPlayable(music.powerUp), music.PlaybackMode.UntilDone)
            game.splash("You reached the goal!")
            game.reset()
        }
    })
```
