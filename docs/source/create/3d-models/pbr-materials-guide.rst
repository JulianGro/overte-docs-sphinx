

###################
PBR Materials Guide
###################

The appearance of a 3D model is controlled by its materials. The materials supported in Overte are physically-based rendering (PBR) materials.
This means that a 3D model's materials will reflect or absorb light (approximately) like how they would in real life.

.. contents:: On This Page
    :depth: 2

------------------------------------------------------
Introduction to Materials, Textures, and Shading
------------------------------------------------------

A 3D model's appearance is controlled by its materials. For example, a 3D model of a key will use a material that determines its color,
how metallic it looks, and if its surface is bumpy or smooth. A 3D model of a brick wall will have material that determines its roughness and color.

Since Overte supports physically-based rendering (PBR) materials, your model will behave like a real world object when exposed to light.
For example, the same 3D model of a key will shine and reflect any light that falls on it. The 3D model of a brick wall will not shine, but will reflect enough light for you to observe its colors and surface.

A material contains texture and shading information.

^^^^^^^^
Textures
^^^^^^^^

Textures are flat images that are applied to 3D models. These add detail on how a 3D model's material looks. For example, a 3D model of a tree trunk will use a bark texture to show what the surface looks like.

Overte supports the use of the following texture formats:

* PNG (recommended)
* JPEG, JPG (recommended)
* TGA
* TIFF, TIF

For best performance, we recommend :doc:`baking all 3D models <../../host/add-content/bake-content>` (including textures) before loading it into Overte.

^^^^^^^
Shading
^^^^^^^

Since Overte supports PBR materials, the shading used depicts an accurate representation of a how light interacts with different material surfaces.
This means that your 3D model will not look the same under different light settings. The PBR shader has a set of material parameters or channels that can be modified to create different types of materials.

.. note:: You can combine shaders with material entities on shape and zone entities to apply shaders to models and avatars.
          This feature was released as an **experimental feature** and has not been thoroughly tested. If you wish to try applying procedural materials to models or avatars *at your own risk*,
          then you can find more information at :doc:`Procedural Shaders for Models and Avatars <../materials/procedural-shaders>`.

**Material Channels**

Material channels determine various parameters such as the roughness or color of a material. You can determine the value of each channel in two ways:

+ **Setting a Value:** The value of a channel is a value set on a slider. Setting a value is like turning off or turning on a switch.
                       For example, if you look at your phone, some parts of it are shiny and some are matte. When you use a value, the entire object reflects that value.
                       If you want different parts of an object to reflect varied roughness, you'll need to use a map.
+ **Using a Map:** The map is an image which you can import to define a property. You will use a map to apply a texture to your 3D model.
                   For instance, your phone may have a case that is matte, but the rest of your phone is shiny. You can use a map to set the case as matte and the phone as shiny.

All materials in Overte have the following channels that determine how they look:

+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Channel Type  | Description                                                                  | Value        | Map         |
+===============+==============================================================================+==============+=============+
| Albedo        | This channel defines the material's color. You can pick any color            | sRGB         | sRGB        |
|               | value of your choice.                                                        |              |             |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Metallic      | This channel determines if the material is metallic or not. You cannot       | [0,1]        | [0,1]       |
|               | have a material that is half metallic, it is either metallic or it isn't.    |              |             |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Roughness     | This determines how rough/matte or glossy/shiny an object is, using          | [0,1]        | [0,1]       |
|               | brightness levels.                                                           |              |             |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Normal        | Normal is a channel that renders an object like there is actual geometry.    | xyz          | bump        |
|               | For instance, normal would add bumps and other irregularities to a stone or  |              |             |
|               | ridges to a sea-shell.                                                       |              |             |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Opacity       | Opacity determines if an object is transparent or opaque.                    | [0,1]        | mask, alpha |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Occlusion     | This property approximates the shading to be as natural as possible. This    | ---          | [0,1]       |
|               | means that it will reproduce how objects interact with light.                |              |             |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Emissive      | This channel controls the amount of light being reflected from an object.    | sRGB         | sRGB        |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Scattering    | Scattering determines how light will behave when it hits human skin. This    | [0,1]        | [0,1]       |
|               | channel details how light is reflected or absorbed by human bodies.          |              |             |
+---------------+------------------------------------------------------------------------------+--------------+-------------+
| Material Type | This channel decides if an object is lit or unlit.                           | [lit, unlit] | ---         |
+---------------+------------------------------------------------------------------------------+--------------+-------------+

Notes:

1. If you set transparency with a texture, the transparency (alpha) must be in the material’s albedo texture, as a PNG file with transparency and *not* as a separate transparency texture.
2. Overte renderer can draw two different kinds of transparency: "alpha" (255 graduates steps of transparency, no shading on surface, casts no shadows,) and "mask" (binary transparency, full shading of opaque surface, whole surface casts shadow.)
3. To determine whether a texture is treated as a mask or as alpha, the engine looks for alpha values between 2% and 98%.
   An easy way to create a mask texture is to save your image as a PNG-8 since it only supports binary transparency, while PNG-24 supports a range of transparency levels.
4. We support using a second UV set with the following texture channels only: Emissive Texture, Normal Map and Ambient Occlusion.

------------------------------------------------------
Sample Materials and Their Textures and Shading
------------------------------------------------------

Overte supports different types of materials. We've created sample objects with each material type.
You can download each object from `this repository <https://github.com/overte-org/hifi_tests/tree/master/assets/models/material_matrix_models/fbx/blender>`_ on GitHub,
or run `this script <https://raw.githubusercontent.com/overte-org/hifi_tests/master/assets/models/material_matrix_models/material_matrix.js>`_ in Overte to upload all sample objects in your domain.


.. FIXME Update this

We've listed all material information (including textures, shading, and channel values and maps) for these sample objects
`here <../../_static/resources/3d-models/Sample_Material_Textures_and_Shading_Guide.html>`_.

---------------------------------------
Set Material Values in Blender
---------------------------------------

.. FIXME Blender has basically completely changed in this regard and the below graphics need to be remade.

.. warning::
    This section is outdated.

When you create a model in Blender, you have to export it in FBX, glTF, GLB or OBJ format to use in Overte. Additionally, you have to modify material properties and textures in Blender to match the PBR material textures in Overte.

Doing so ensures that your model appears how you intend it to.

By default, any material property set with a texture will override a property set with a value. The only exception to this is in the case of vertex color and a texture,
in which case the vertex color and texture will multiplied together. This can be useful for creating highly performant colored models using grey-scale textures and vertex colors.

We've included images where the fields corresponding to each supported PBR channel in Blender are highlighted, along with details about which values and colors correspond to the range corresponding with that channel.
It should be noted that models exported as OBJ may not have full PBR material support in Overte yet.

.. image:: _images/material-textures-b.jpg

.. image:: _images/material-values-b.jpg

--------------------------------
Set Material Values in Maya
--------------------------------

.. FIXME Maya has not been in use by anyone in the community so this section might or might not be outdated.

.. warning::
    This section hasn't been tested in a long while and might be outdated.

Use the graphics below to set the right material values and textures in Maya.

.. image:: _images/material-values-m.jpg

.. image:: _images/material-textures-m.jpg


**See Also**

+ :doc:`Bake Your Content Using the Oven <../../host/add-content/bake-content>`
+ :doc:`Add a Material Entity <../entities/material-entity>`
