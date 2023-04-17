****************
Silicon Labs IDE
****************

Overview
********

The Silicon Labs IDE is a free software development environment for the C8051F02x family of microcontrollers. It is a cross-platform IDE that can be used on Windows, Linux, and Mac OS X. The IDE is based on the Eclipse platform and is written in Java. The IDE is available for download from the Silicon Labs website.

----------------

Software Installation
*********************

.. _installation:

There are two software packages that you will need in order to develop code for the C8051F020 boards. The first is the Silicon Labs IDE (IDE stands for "Integrated Development Environment"). This code is no longer openly supported by Silicon Labs but it can be found if you have the right link. The link below should get you where you need to be:

The second software package you will need is Keil PK51. This package contains the tool chain (i.e. the compiler, assembler and linker) that you will need to translate your source code into a program the C8051F020 understands.

Both of these software packages are available at the following link:

This is a link to a reference document for the `Silicon Labs`_.

.. _Silicon Labs: https://www.silabs.com/developers/8-bit-8051-microcontroller-software-studio

----------------

Creating project
****************

.. _project:

#. Open Silicon Labs IDE
#. Select "Project" -> "New Project" from menu

    .. image:: images/new_project_menu.PNG
      :width: 500
      :height: 350
      :alt: Menu

#. Under the table "Project"

    * Select "C8051F02x" as device family
    * Create a memerable name for the project
    * Select the file location for the project
    * Select "Project Type".

#. Click "Okay" to create the project

----------------


