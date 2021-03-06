<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Levels of Detail (LOD)

<sub>[previous](../bathtub-material/README.md#user-content-bathtub-test-material) • [home](../README.md#user-content-ue4-static-meshes) • [next](../pivot-point/README.md#user-content-pivot-point)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Levels of detail (LOD) are standard practice to apply when creating models in 3-D games. When an object gets further in a scene less detail is required in both the texture maps and the geometry to accurately represent the model in the scene. This way since most models are far away from the camera we can reduce our total vertice count and the size of our large textures by having lower resolution versions.

<br>

---


##### `Step 1.`\|`SUU&G`|:small_blue_diamond:

So a different model is loaded based on how far away from the camera the model is. This is called LOD's and is very common in real time simulations to make the game look better and run faster.

![alt_text](images/image_124.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Download and open in Maya [SM_Sphere_LOD.fbx](../Assets/SM_Sphere_LOD.fbx). You will have a **SM_Sphere** and an **SM_Sphere1**.  These are the same two spheres as previous but are in the same file.  We will use the higher poly one when the camera is close and the lower poly one when the camera is far from the sphere.  Press **contrl H** and **shift H** to hide and show the two models.  You need to make sure both models are in the same world space and that the pivot is in the same place.  I have two spheres here right on top of each other.

https://user-images.githubusercontent.com/5504953/129810965-107fab0f-a51d-4578-9b24-7fd9e3d9dc8a.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I select in **Object Mode** the highest poly model first then the next level in order from highest detail to smallest.  I press the **Edit | LOD Level of Detail | Create LOD Group**.

https://user-images.githubusercontent.com/5504953/129811510-29e749ea-4f69-421e-b307-a2f7c3fb1b6c.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up the **Outliner** and expand the **LOD_Group_1** and look at the LOD's.  I can see the change of model LOD's when zooming in and out of Maya.

https://user-images.githubusercontent.com/5504953/129811684-5ec8e094-ab03-4729-919d-a9ae3c024746.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SUU&G`| :small_orange_diamond:

Use the **File | Game Exporter** option in Maya.  We have only one change to our base settings.  The levels of detail will NOT export wihtout having **Animation** selected.  So select this and then also select **Smoothing Groups** and **Triangulate**.  Pick a **Path** and call it `SM_SphereLOD`. Press the <kbd>Export</kbd> button.

![alt_text](images/ModelLOD.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond:

Drag this file from the operating system folder into the content browser. A message should appear saying the object is being imported. Now an **FBX Import Options** menu appears.    You HAVE to set **Import Mesh LODs** to true for it to work.
 
![check off import mesh LODs on import](images/ImportModel.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

You should now see a static mesh called **SM_Sphere_LOD** that has only one image of a sphere in it (so it is not two objects).

![single model imported](images/SingleModelImported.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **SM_Sphere_LOD** and you can switch between the two models as it is loaded as one. You can change **LOD** between `LOD 0` and `LOD 1`. Return it to `LOD Auto` so we can see it in the preview window.

https://user-images.githubusercontent.com/5504953/129813840-364f91f2-79b6-4936-8c48-6b85d30feaea.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:
Unreal automatically tried to figure out when to go from **LOD 0** to **LOD 1**. If you zoom in and out you can see that it switches almost right away to the lower poly version.

https://user-images.githubusercontent.com/5504953/129814208-e0545a1d-54a5-47e3-a039-e5888f3644fa.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SUU&G`| :large_blue_diamond:

Now you can see the **Current Screen Size** on the menu in the corner of the preview window.  This way I can look and see at what point I want to switch the **LODs**.  I think `0.1` makes a good value.  First I turn off **Auto Compute LOD Distance** then I change the **LOD 0 | Screen Size** to `0.1`.  I then move back and forth and we can see the change. 

![change lod 0 size to .1](images/ChangeLODSize.jpg)

https://user-images.githubusercontent.com/5504953/129814924-a173fa79-6d8d-4cfc-9cfd-8e73a45f222f.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: 

Now we can make the transition almost invisible by assigning materials custom built for the spheres.  Oh yeah, we did these earlier on in the demo. We can assign **Material Element 0** with `M_Rough` and **Material Element 1** with `M_Rough_Normal`.

![alt_text](images/MaterialAddition2.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now with a combination of **LODs** and **Normal Mapping** we have reduced our poly count when the ball is further away with practically no visual degradation.

https://user-images.githubusercontent.com/5504953/129815505-66b33d62-781a-4024-8c7a-5af938742c61.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now you do not have to always make the **LODs** by hand in modelling software.  In many cases you can use **Unreal's** automatic tools to create a set for you based on the high poly model.  You can then customize which levels they take in engine based on its use.

Lets try this out on our first sphere that has only one model.  Open up **SM_High_Poly_Sphere** and select **LOD Settings | LOD Group | Large Prop**.  There are different default settings for the creation of LOD's based on a single static mesh.  You can even author your own if you have specific settings. 

![alt_text](images/AutoLOD.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

We get a pop up as this is a destructive setting. It will get rid of the current LOD's and create new ones based on the LOD group LargeProp.  Since we have no LODs there is nothing to undo and we want to see the result so press the <kbd>Yes</kbd> button.

![lod group message](images/LODGroupMessage.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: 

You should now see 4 automatically created LOD's (LOD 0, 1, 2, 3).  Now this sphere was too big in the first place.  It really doesn't degrade in it form when viewing the LOD's.  We could actually create even more LOD's then degrade them further.  But for now lets accept that going from ~80k tris to ~9 tris is a good optimization.

![4 automatically created LODs](images/4AutoLODs.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

For any of the automatically created LOD levels, we can either delete them or change their settings (have them degrade more or less based on when you are switching levels of details).

![custom lod settings](images/CustomizeLODSettings.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Move back and forth and look at the stats in the top left corner.  You will see that the LOD's are switching be we do not see it in the preview window it is invisible.  Make sure you are on **LOD Auto** otherwise you will not be able to preview the switching.

https://user-images.githubusercontent.com/5504953/129864167-3109711d-6dbe-44b8-824d-faa2d4bbc5db.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Duplicate the floor. Drag a copy of **SM_SphereLOD** on top of this new piece of floor.  Press the <kbd>Build</kbd> to buiold our static lighting.

![dupe floor and place sm_spherelod on ground](images/CreateLODIsland.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now for debugging sometimes it is better to start the game when playing at the current location rather than going back to the **Player Start** location.  You can set this by selecting the **Triangle** by the <kbd>Play</kbd> button and selecting `Spawn Player At | Current Camera Location`.

![spawn player from current camera location](images/PlayFromCurrentLocation.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`SUU&G`| :large_blue_diamond: :large_blue_diamond:

Lets look at the LOD's in game now.

https://user-images.githubusercontent.com/5504953/129865894-7ad0778a-1787-4988-bacd-81270dc70c45.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`SUU&G`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Save and commit the work to the repository.  Submit to **GitHub**.

https://user-images.githubusercontent.com/5504953/129867018-4e7d8cae-aa45-4592-af39-a6d987ffb71e.mp4

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Pivot Point">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../bathtub-material/README.md#user-content-bathtub-test-material)| [home](../README.md#user-content-ue4-static-meshes) | [next](../pivot-point/README.md#user-content-pivot-point)|
|---|---|---|
