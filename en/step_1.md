In the Inspector window for the GameObject, click ‘Add Component’ and choose CharacterController. Position and size the controller so it covers the whole of your follower GameObject.

![The Inspector window showing the Character Controller component.](images/path.png)

![The Scene view showing the Dog GameObject with Character Collider highlighted around the frame of the Dog.](images/path.png)

**Tip:** Press ‘shift’ + ‘f’ to focus on the follower GameObject in the Scene view .

Click on ‘Add Component’ and add a Box Collider. Adjust the Center Y and Size Y values so that other characters cannot walk through or climb on top of the follower GameObject:

![The Inspector window showing the Box Collider component with Cener Y and Size Y properties highlighted.](images/path.png)

Go to the ‘Add Component’ button  again and add a second ‘Box Collider’ to the follower GameObject.

This Box collider will use ‘IsTrigger’ to make the follower GameObject move if the Player gets close enough to draw the followers attention. This Box collider needs to be big enough that the Player can’t easily sneak past:

![The Box Collider component with 'Is Trigger' ticked, Center Y = 0.5 and Size X=3, Y=1, and Z=3.](images/path.png)

![The Scene view showing the dog with Character Collider fitting around it's body and the Box Collider much larger on the X and Y axis.](images/path.png)

**Tip:** You will also need to add Box Colliders to the any other GameObjects that could move into the patrol area. These Box Colliders will not have 'Is Trigger' checked.

Click on ‘Add Component’ and add a ‘New script’ then give your script a sensible name.

Double-click on your new script to open it in the code editor.

Create a variable to store whether or not the follower GameObject is following the Player:

```
bool isFollowing = false;
```

Create an `OnTriggerEnter()` method to change the state of the variable if the Player gets close:

```
void OnTriggerEnter(Collider other)
{
    if (other.gameObject.tag == "Player")
    {
        IsFollowing = true;
    }
}
```
