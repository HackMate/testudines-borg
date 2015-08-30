# testudines-borg
My computercraft playground. Basically my work in progress in order to create a testudines borg collective.

    Intellij CC-Api:
    http://www.computercraft.info/forums2/index.php?/topic/12530-intellij-idea-120-cc-library-for-lua-addon/
    
    Guidelines:
        Try to use Object Orientation, preferably Closure-based classes
            For a comparison of Table- versus Closure-based classes see: http://lua-users.org/wiki/ObjectOrientationTutorial 
    
    
Ideas:

Resumable? Task.findHome() => Pathfinder(body(map), map).gotTo(homePos)
- pathfinder (body, map)
    - goTo(position: Position)

- body provides movementHandler, inspectionHandler and inventoryHandler apis
    - Propagates api calls
        - Example: refuel() -> inventoryHandler, movementHandler

- movementHandler (map) - handles movement
    - tracks position and fuel level (persists it)
    - orientates itself if necessary (detects facing)
    - has a map that it updates upon successful movement
    - Provides API
        - turnLeft()
        - turnRight()
        - turnAround()
        - forward()
        - back()
        - up()
        - down()
        - position() = position
        - orientate() = position.facing
        - refuel(number quantity)
        - getFuelLevel()

- inspectionHandler (knownItems) has a list of items where it adds types that it encounters
    - Provides API
        - inspectUp()
        - inspectDown()
        - inspect()
        - compare()
        - compareUp()
        - compareDown()
        - compareTo(slotNumber)

- inventoryHandler(inventory) - tracks the content of the inventory
    - suck()
    - suckUp()
    - suckDown()
    - drop()
    - dropUp()
    - dropDown()
    - selectFuel()
    - refuel()
    - transferTo()
    - sortInventory()
    