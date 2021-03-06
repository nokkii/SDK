<div align=right><img src="../Tools/imgs/xim.png" ></div>
<h1> Unity SDK FAQ</h1>


**1. How to Get Controllers Positions and Rotations?**

> * You can simply get a reference to a TrackedObject and then grab the transform infomation by using

        public virtual void GetTransform(ref Vector3 position, ref Quaternion rotation);

> * You can also get transform data with ControllerInput class.

        using UnityEngine;
        using Ximmerse;
        using Ximmerse.InputSystem;
      
        class TestClass : MonoBehaviour
        {
            void Update()
            {
                ControllerInput lc = ControllerInputManager.instance.GetControllerInput(ControllerType.LeftController);
      
                Vector3 position = lc.GetPosition();
                Quaternion rotation = lc.GetRotation();
            }
        }

&emsp;

**2. How to Get Head Position and Rotation?**

> It is recommened to use `TrackedHead.target` to grab the head transform information,
because head position requires complex calculation, which is already done in `TrackHead.cs` script.

&emsp;

**3. How to Get Button Press/Down/State?**

> First of all, you need a reference to a `ControllerInput`. Example can be found [here](https://github.com/Ximmerse/SDK/blob/master/Unity/APIDoc.md).

> Then all you need to do is using `GetButton`/`GetButtonUp`/`GetButtonDown` functions implemented in the `ControllerInput` class. Details can be found [here](https://github.com/Ximmerse/SDK/blob/master/Unity/APIDoc.md).

**4. How to setup 3Dof demo working?**
> We have provided a 3Dof controller sample project in the Unity SDK. To get it working properly, please follow the steps below:
> 
>1. Go to Ximmerses Setting Panel and make sure Ximmerse Device is set to Daydream Controller. This is option to use Ximmerse controller in a similar way to Daydream 3dof controllers.
>	<div align=left><img src="../Tools/imgs/3dof_setting.png" ></div>
>2. Go to VR Gallery scene. Set VRCameraRig positon to 0,0,0. 
>	<div align=left><img src="../Tools/imgs/3dof_set_to_zero.png" ></div>
>
>3. Set _UIRayCaster objects to active. 
>	<div align=left><img src="../Tools/imgs/3dof_set_active.png" ></div>
>
>4. Build the project to your target platform and use your controllers to pick colors. 
>

**5. How to Integrate Daydream SDK with Ximmerse SDK?**
> [![IMAGE ALT TEXT HERE](../Tools/imgs/daydream_sdk_integration.png)](https://www.youtube.com/watch?v=d6YVdRvNGfw)