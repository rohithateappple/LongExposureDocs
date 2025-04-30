# Getting Started  

Using the Long Exposure Component is quite simple. You can either attach the component directly to any blueprint of your choice or simply drag and drop the ``BP_LongExposureActor`` into the scene. By default, the component uses SPACE as input to start capture.

## Using the Component

1. Go to your actor of choice. In the **Components** section, add the ``BP Long Exposure Component``.

    ![alt text](<images/Screenshot 2025-04-30 131202.png>)

2. Once the actor is placed in the scene, press **SPACE** to start capture. (Input logic resides within ``BP_LongExposureCamera``).

    ![alt text](<images/Screenshot 2025-04-30 131646.png>)

3. The capture will last the duration of ``ExposureTime``. You can change this variable via the details panel of the component. 1 second = 10 units.

    ![alt text](<images/Screenshot 2025-04-30 131822.png>)

4. The logic for this component is located in ``Plugins/LongExposureCamera Content/Blueprints/BP_LongExposureCamera``. If you need to make changes, feel free to do so here.

    ![alt text](<images/Screenshot 2025-04-30 132817.png>)

## Using BP_LongExposureActor

Ideal for prototyping where you need to see the effects quickly.

1. Go to `Plugins/LongExposureCamera Content/Blueprints/` and drag `BP_LongExposureCamera` into the level. 
2. Once again press **SPACE** to start capture.

## Discrete Trails vs Smooth Trails

Two artistic effects can be achieved by controlling the motion blur of the component. If motion blur is turned off completely you can achive a discrete long exposure effect. 

![alt text](<Screenshot 2025-04-30 143748.png>)

![alt text](<images/Screenshot 2025-04-30 144105.png>)


If the motion blur is turned on, you can achieve smooth exposure depending on the motion blur settings.

![alt text](<images/Screenshot 2025-04-30 144149.png>)

## Blend Methods

Currently the plugin offers four blend methods to create various exposure effects. The blend mode can be set in the details panel of the component.

![alt text](<Screenshot 2025-04-30 145440.png>)

1. Max

    Picks the brightest sample over the accumulated frames. Best suited for light trails and other effects requiring strong trail presence. It recreates how regular cameras work in open shutter with lowered exposures.

    ![alt text](<images/Screenshot 2025-04-30 150338.png>)

2. True Mean

    True Mean is a recreation of Photoshop's mean blending. It takes the average of all accumulated frames resulting in smooth "milky" frames. Best suited for smoothing out clouds, water bodies and other large areas of movement. This is however not ideal for capturing rapid movement, as they will be averaged out quite quickly.

    *1st Frame*

    ![alt text](<images/Screenshot 2025-04-30 150802.png>)
    
    *500th Frame*

    ![alt text](<images/Screenshot 2025-04-30 150748.png>)


3. Lerp

    Basic linear interpolation of accumulated frames. Results vary depending on the Lerp Alpha.

    ![alt text](<images/Screenshot 2025-04-30 150921.png>)

4. Median

    Takes Max and Min into account with a bias towards Max.

    ![alt text](<images/Screenshot 2025-04-30 151110.png>)


## Rendering Using Movie Render Queue

To render your capture, you'll need UE's built-in **Movie Render Queue** plugin. 

![alt text](<images/Screenshot 2025-04-30 152540.png>)

In the **Movie Render Queue** settings, add a **UI Renderer** and a **Command Line Encoder**. Once this is done, hit render and enjoy!

![alt text](<images/Screenshot 2025-04-30 152703.png>)

## Closing Note

The bulk of the effects result from one material called ``M_LongExposureBlend`` located in ``Plugins/LongExposureCamera Content/Materials/``. This material controls the nature of blending and because of that, a lot of customizations can be done here to suit your needs. 

![alt text](<images/Screenshot 2025-04-30 151724.png>)