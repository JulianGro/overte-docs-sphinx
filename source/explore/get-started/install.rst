################
Install Overte
################

Overte has two different installers. The *Client Installer* comes with everything you need to view and interact with Overte's content and users.
However, you are unable to host content using this installer. The *Client + Server Installer* has everything the client installer does,
but it also enables you to :doc:`host your own content <../../host>` and share it with the world.
The Client + Server Installer download is only provided for Windows. For Linux see: :doc:`Host a Domain from a Local or Cloud Linux Server <../../host/server-setup/linux-server>`.

.. contents:: On This Page
    :depth: 2

-------------------
System Requirements
-------------------

In order to run Overte, ensure that your computer meets these system requirements:

* Operating system:

  * Windows 8.1 64-bit, Windows 10 64-bit, or Windows 11 64-bit
  * Ubuntu 18.04 64 bit, or most other modern Linux distributions

* CPU:

  * **Minimum:** Dual-core with hyper-threading
  * **Recommended:** Quad-core with hyper-threading or better

* System memory:

  * **Minimum:** 8GB

* Graphics adapter:

  * **Minimum:** Nvidia 600 series
  * **Recommended:** Nvidia 900 series or higher
  * **Minimum:** AMD Radeon HD 87XX series
  * **Recommended:** AMD Radeon HD 89XX series or higher
  * **Minimum:** Intel 5th generation CPU integrated Iris graphics. Using Intel integrated graphics is not recommended.

.. note:: The listed graphics adapters support OpenGL 4.1 and above. This is a requirement for any graphics adapter running Overte.

In addition, your network must have enough internet bandwidth to run Overte:

* If you are using Interface only to explore the metaverse, then you should have Internet speeds of at least **10 Mbit/s download** and **2 Mbit/s upload**.
* If you are hosting a domain server on a remote machine or your local computer, you need to add **10 Mbit/s upload** for each user that
  you want to allow to concurrently visit your domain. You will need only **2 Mbit/s upload** per user if you host your assets on an external web server rather than your domain server.

.. note:: A world that is specifically built for low-end systems might run fine on a system with slightly less memory or a lower CPU core count.

.. note:: Running Overte on a high resolution display or in VR mode will need a much better graphics adapter, depending on your display's resolution and targeted frame rate.

-----------------------------------
Download Overte
-----------------------------------

The current release is available to `download on our website <https://overte.org/#downloads>`_.

If you intend to use Overte in VR mode with an HMD, ensure that SteamVR or Oculus Runtime is also installed on your system before launching Overte.
VR mode is not supported on macOS. The Oculus Runtime is not supported on Linux.


---------------------------------
Install Overte
---------------------------------

Once you've downloaded the installer, you're ready to install Overte. The process will be different based on your operating system:

^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Windows Install
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To install on Windows, simply double-click on the downloaded installer file to open it. Run through the prompts on the installer.
Once you finish the install process, Interface will open, and you will be able to log in and begin exploring the metaverse.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Mac Install
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

At this time, the Overte installer for Mac is unsigned, so you will need give the OS permission to install the application.

1. Open the downloaded installer dmg file.
2. Agree to the License Agreement.
3. Drag Overte to the Applications folder.
4. Try opening Interface.app. You will be prompted that macOS will not open the file because it is unsigned.
5. Open **System Preferences > Security & Privacy**. On older macOS versions this might be in **System Preferences > General**.
6. Next to the warning indicating that Interface is blocked, click 'Open Anyway'.
7. Confirm that you want to open the application.
8. Allow microphone access if prompted, in order to be able to talk inside the application.

At this point, Interface will open and you will be able to log in and begin exploring the metaverse.


^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Linux Install
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Mark the downloaded AppImage file as executable. (for example, with ``chmod +x Overte-x86_64_20220219.AppImage``.)
2. (Optional) If you want the AppImage to be integrated into your system, install `AppImageLauncher <https://github.com/TheAssassin/AppImageLauncher>`_.
3. Execute AppImage.

Currently the server is not part of the Linux Interface AppImage. To host a domain, please refer to :doc:`Host a Domain from a Local or Cloud Linux Server <../../host/server-setup/linux-server>`.

----------------------------
Upgrade Overte
----------------------------

Overte is always changing, as we work to improve performance and add features that will enhance your experience in the metaverse.
At any time, you can download the latest release from our `website <https://overte.org/#downloads>`_.

You cannot upgrade Overte on Windows if you have Overte Interface or Server running on your computer. Be sure to quit these applications before upgrading.
Keep in mind that Overte Server could be running in the background.

For Windows, locate the Overte app in your system tray. Right-click on the icon and select 'Quit'. Alternatively, end the 'server-console' background process using the Task Manager.

For more information on the latest releases, see our :doc:`Release Notes <../../release-notes>`.


---------------------------------
Perform a Clean Install
---------------------------------

If you're facing problems when you load Interface or the local Server, then you can try performing a clean install.
A clean install removes multiple files and settings that you may need once you install Overte again.

.. note:: Ensure that you back up the following files before a clean install: Favorites, Wearables, Server content, and Entities. These settings will be deleted during the clean install.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Windows Clean Install
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Click on the Start menu and type "Add or Remove Programs" in your Windows search bar.
2. Uninstall any versions of Overte that are visible.
3. Once Overte is uninstalled, browse to your %Program Files% directory. Delete all folders related to Overte.

.. warning::

    The next 3 steps will permanently delete your local Server's content. If you wish to keep this content,
    copy %AppData%/Local/Overte/assignment-client to another location on your computer before proceeding.
    Repeat for %AppData%/Roaming/Overte/assignment-client.

4. Browse to your local %AppData% folder (usually ``C:/Users/<your_username>/AppData/Local``). If you do not see the folder,
   make sure you can view hidden folders: in File Explorer, click View and make sure "Hidden Items" is checked. Delete all folders related to Overte.
5. Browse to your roaming %AppData% folder (usually ``C:/Users/<your_username>/AppData/Roaming``). Delete all folders related to Overte.
6. Re-install Overte using the steps above. To restore your local Server's content, copy the ``assignment-client`` folders you previously saved back into to their respective locations.

^^^^^^^^^^^^^^^^^^^^^^^^
Mac Clean Install
^^^^^^^^^^^^^^^^^^^^^^^^

1. Open your Applications folder and delete the Overte folder.
2. Open the ``<username>/.config`` folder. This is a hidden folder than is accessible by going to *Go > Home*. Press the keyboard shortcut ``Command + Shift + .`` (period).
3. Delete the ``overte.org`` folder.
4. Open the ``~/Library`` folder by holding the Option key and clicking the 'Go' menu while in the Finder. The Library option should appear in the menu.
5. Browse to ``~/Library/Application Support`` and delete the Overte folder.
6. Empty the Trash.
7. Re-install Overte using the steps above.


**See Also**

+ :doc:`Install Your Domain <../../host/server-setup>`
