.. _plugins_organisation_pmrWorkspacesWindow:

============================
 PMRWorkspacesWindow plugin
============================

The PMRWorkspacesWindow plugin gives you access to your `PMR <https://models.physiomeproject.org/>`__ workspaces.
By default, it looks as follows:

.. image:: pics/PMRWorkspacesWindowScreenshot01.png
   :align: center
   :scale: 25%

The following topics are covered:

- :ref:`Instances of PMR <plugins_organisation_pmrWorkspacesWindow_instancesOfPmr>`
- :ref:`Specify an instance of PMR <plugins_organisation_pmrWorkspacesWindow_specifyInstanceOfPmr>`
- :ref:`Log on to PMR <plugins_organisation_pmrWorkspacesWindow_logOnToPmr>`
- :ref:`Make a local copy of a public workspace <plugins_organisation_pmrWorkspacesWindow_makeLocalCopyPublicWorkspace>`
- :ref:`Create a new workspace <plugins_organisation_pmrWorkspacesWindow_createNewWorkspace>`
- :ref:`Synchronise with PMR <plugins_organisation_pmrWorkspacesWindow_synchroniseWithPmr>`

.. _plugins_organisation_pmrWorkspacesWindow_instancesOfPmr:

Instances of PMR
----------------

There are three instances of `PMR <https://models.physiomeproject.org/>`__:

- `Models instance <https://models.physiomeproject.org>`__: everything on this instance is permanent and persistent.
  It is always up and always stable.
- `Staging instance <https://staging.physiomeproject.org>`__: it is used for public testing/preview of PMR developments.
  Data on this instance is wiped periodically whenever a new public testing/preview of the PMR software suite is released for the required testing exercise.
- `Teaching instance <https://teaching.physiomeproject.org>`__: the functionality of this instance should match the models instance, but without the data persistency guarantees.
  While data on this instance is also not permanent, any wipes to data stored will be announced on the `cellml-discussion mailing list <https://lists.cellml.org/sympa/info/cellml-discussion>`__.

Both the `models instance <https://models.physiomeproject.org>`__ and the `teaching instance <https://teaching.physiomeproject.org>`__ require you to create an account before you can start interacting with them.
On the `staging instance <https://staging.physiomeproject.org>`__, your `models instance <https://models.physiomeproject.org>`__ account may work, but if not then you need to create an account on the `staging instance <https://staging.physiomeproject.org>`__.

.. _plugins_organisation_pmrWorkspacesWindow_specifyInstanceOfPmr:

Specify an instance of PMR
--------------------------

You can specify which instance of `PMR <https://models.physiomeproject.org/>`__ to use by clicking on the |oxygenCategoriesPreferencesSystem| button in the tool bar, or by selecting the ``Tools`` | ``Preferences...`` menu item and then the **PMRSupport** section:

.. |oxygenCategoriesPreferencesSystem| image:: ../../pics/oxygen/categories/preferences-system.png
   :class: inlineicon
   :width: 16px

.. image:: pics/PMRWorkspacesWindowScreenshot02.png
   :align: center
   :scale: 25%

This is also where you must specify your name and email address, if you want to be able to :ref:`synchronise <plugins_organisation_pmrWorkspacesWindow_synchroniseWithPmr>` your workspaces with `PMR <https://models.physiomeproject.org/>`__.

.. _plugins_organisation_pmrWorkspacesWindow_logOnToPmr:

Log on to PMR
-------------

To log on to `PMR <https://models.physiomeproject.org/>`__, you need to click on the |logOn| button in the tool bar.
This brings up a window inviting you to log in to `PMR <https://models.physiomeproject.org/>`__:

.. |logOn| image:: pics/logOn.png
   :class: inlineicon
   :width: 16px

.. image:: pics/PMRWorkspacesWindowScreenshot03.png
   :align: center
   :scale: 25%

Logged in, you can grant OpenCOR access to `PMR <https://models.physiomeproject.org/>`__ by clicking on the ``Grant access`` button:

.. image:: pics/PMRWorkspacesWindowScreenshot04.png
   :align: center
   :scale: 25%

This closes the window and replaces the |logOn| button with the |logOff| button, and displays a message indicating that no workspaces were found:

.. |logOff| image:: pics/logOff.png
   :class: inlineicon
   :width: 16px

.. image:: pics/PMRWorkspacesWindowScreenshot05.png
   :align: center
   :scale: 25%

.. _plugins_organisation_pmrWorkspacesWindow_makeLocalCopyPublicWorkspace:

Make a local copy of a public workspace
---------------------------------------

The :ref:`PMR window <plugins_organisation_pmrWindow>` lists published exposures, which reference a specific state of a public workspace.
Say that you want to experiment with the `Hodgkin–Huxley model <https://ncbi.nlm.nih.gov/pmc/articles/PMC1392413/pdf/jphysiol01442-0106.pdf>`__.
You can do so by switching to the teaching instance (see :ref:`above <plugins_organisation_pmrWorkspacesWindow_specifyInstanceOfPmr>`), looking for the `Hodgkin–Huxley model <https://ncbi.nlm.nih.gov/pmc/articles/PMC1392413/pdf/jphysiol01442-0106.pdf>`__, right clicking on it and by selecting the ``Make Local Copy...`` menu item:

.. image:: pics/PMRWorkspacesWindowScreenshot06.png
   :align: center
   :scale: 25%

You need to provide the path to an *empty* folder.
The local copy completed, you can double click on it to reveal its contents:

.. image:: pics/PMRWorkspacesWindowScreenshot07.png
   :align: center
   :scale: 25%

.. _plugins_organisation_pmrWorkspacesWindow_createNewWorkspace:

Create a new workspace
----------------------

You can create a workspace by clicking on the |newFolder| button in the tool bar.
You need to provide both a name and the path to a folder (it *does not* have to be an empty folder).
You may also provide a description:

.. |newFolder| image:: ../../pics/newFolder.png
   :class: inlineicon
   :width: 16px

.. image:: pics/PMRWorkspacesWindowScreenshot08.png
   :align: center
   :scale: 25%

Any file already present in the folder will be considered new.
For example, if you provide a folder containing the `models <https://github.com/opencor/opencor/tree/master/models/>`__ shipped with OpenCOR, you will get something like the following upon creation of the workspace:

.. image:: pics/PMRWorkspacesWindowScreenshot09.png
   :align: center
   :scale: 25%

The model files are preceded by the |waFile| icon, meaning that they are indeed new, while the workspace folder is preceded by the |unstagedOwnedWorkspace| icon, meaning that it is owned by you and that it contains changes that have yet to be synchronised with `PMR <https://models.physiomeproject.org/>`__ (see :ref:`below <plugins_organisation_pmrWorkspacesWindow_icons>` for a full list of possible icons).

.. |waFile| image:: pics/waFile.png
   :class: inlineicon
   :width: 16px

.. |unstagedOwnedWorkspace| image:: pics/unstagedOwnedWorkspace.png
   :class: inlineicon
   :width: 16px

.. _plugins_organisation_pmrWorkspacesWindow_synchroniseWithPmr:

Synchronise with PMR
--------------------

Your workspace created, you may want to syncrhonise it with `PMR <https://models.physiomeproject.org/>`__.
This is done by right clicking on any of the files/folders in your workspace and by selecting the ``Synchronise Workspace With PMR...`` menu item.
This brings up a window where you can see *which* files have changed and *what* exactly has changed.
For `CellML <https://cellml.org/>`__ files, changes can be seen using either the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>` or the raw CellML format (i.e. `XML <https://w3.org/XML>`__-based).
Simply toggle the |cellmlLogo| button as needed:

.. |cellmlLogo| image:: ../../pics/cellmlLogo.png
   :class: inlineicon
   :width: 16px

.. image:: pics/PMRWorkspacesWindowScreenshot10.png
   :align: center
   :scale: 25%

Provide a description for your changes and click on the ``OK`` button to synchronise your workspace with `PMR <https://models.physiomeproject.org/>`__.
The model files are now preceded by the |file| icon and the workspace folder by the |ownedWorkspace| icon:

.. |file| image:: pics/file.png
   :class: inlineicon
   :width: 16px

.. |ownedWorkspace| image:: pics/ownedWorkspace.png
   :class: inlineicon
   :width: 16px

.. image:: pics/PMRWorkspacesWindowScreenshot11.png
   :align: center
   :scale: 25%

You can check your workspace in `PMR <https://models.physiomeproject.org/>`__ by right clicking on any of the files/folders in your workspace and by selecting the ``View Workspace In PMR...`` menu item:

.. image:: pics/PMRWorkspacesWindowScreenshot12.png
   :align: center
   :scale: 25%

If you modify the model files and decide to resynchronise your workspace with `PMR <https://models.physiomeproject.org/>`__, you will see something like the following where all the model files have been selected.
This allows you to see all their changes at once, be they additions (in green) or deletions (in red):

.. image:: pics/PMRWorkspacesWindowScreenshot13.png
   :align: center
   :scale: 25%

Your workspace resynchronised, you can see the history of your changes in `PMR <https://models.physiomeproject.org/>`__:

.. image:: pics/PMRWorkspacesWindowScreenshot14.png
   :align: center
   :scale: 25%

Tool bar
--------

| |toolBarNewFolder|                         Create a new workspace
| |toolBarOxygenActionsViewRefresh|          Reload the list of workspaces
| |toolBarOxygenCategoriesPreferencesSystem| Preferences for PMR support
| |toolBarLogOn|                             Log on to PMR
| |toolBarLogOff|                            Log off from PMR

.. |toolBarNewFolder| image:: ../../pics/newFolder.png
   :class: toolbar
   :width: 24px

.. |toolBarOxygenActionsViewRefresh| image:: ../../pics/oxygen/actions/view-refresh.png
   :class: toolbar
   :width: 24px

.. |toolBarOxygenCategoriesPreferencesSystem| image:: ../../pics/oxygen/categories/preferences-system.png
   :class: toolbar
   :width: 24px

.. |toolBarLogOn| image:: pics/logOn.png
   :class: toolbar
   :width: 24px

.. |toolBarLogOff| image:: pics/logOff.png
   :class: toolbar
   :width: 24px

.. _plugins_organisation_pmrWorkspacesWindow_icons:

Icons
-----

Different icons are used to distinguish between the different states of a workspace:

.. table::
   :class: icons

   +-------------------------+---+------------------------------+---------------------------------------------------+
   | |iconWorkspace|         | / | |iconOwnedWorkspace|         | Public/owned workspace                            |
   +-------------------------+---+------------------------------+---------------------------------------------------+
   | |iconStagedWorkspace|   | / | |iconStagedOwnedWorkspace|   | Public/owned workspace with *staged* changes.     |
   +-------------------------+---+------------------------------+---------------------------------------------------+
   | |iconUnstagedWorkspace| | / | |iconUnstagedOwnedWorkspace| | Public/owned workspace with *unstaged* changes    |
   +-------------------------+---+------------------------------+---------------------------------------------------+
   | |iconConflictWorkspace| | / | |iconConflictOwnedWorkspace| | Public/owned workspace with *conflicting* changes |
   +-------------------------+---+------------------------------+---------------------------------------------------+

.. |iconWorkspace| image:: pics/workspace.png
   :class: icon
   :width: 24px

.. |iconStagedWorkspace| image:: pics/stagedWorkspace.png
   :class: icon
   :width: 24px

.. |iconUnstagedWorkspace| image:: pics/unstagedWorkspace.png
   :class: icon
   :width: 24px

.. |iconConflictWorkspace| image:: pics/conflictWorkspace.png
   :class: icon
   :width: 24px

.. |iconOwnedWorkspace| image:: pics/ownedWorkspace.png
   :class: icon
   :width: 24px

.. |iconStagedOwnedWorkspace| image:: pics/stagedOwnedWorkspace.png
   :class: icon
   :width: 24px

.. |iconUnstagedOwnedWorkspace| image:: pics/unstagedOwnedWorkspace.png
   :class: icon
   :width: 24px

.. |iconConflictOwnedWorkspace| image:: pics/conflictOwnedWorkspace.png
   :class: icon
   :width: 24px

Similarly, different icons are used to distinguish the different states of a file:

.. table::
   :class: icons

   +--------------+---+--------------+-----------------------------------------------+
   |              |   | |iconFile|   | File that is *clean*                          |
   +--------------+---+--------------+-----------------------------------------------+
   | |iconIaFile| | / | |iconWaFile| | Staged/unstaged file that has been *added*    |
   +--------------+---+--------------+-----------------------------------------------+
   | |iconIdFile| | / | |iconWdFile| | Staged/unstaged file that has been *deleted*  |
   +--------------+---+--------------+-----------------------------------------------+
   | |iconImFile| | / | |iconWmFile| | Staged/unstaged file that has been *modified* |
   +--------------+---+--------------+-----------------------------------------------+
   | |iconIrFile| | / | |iconWrFile| | Staged/unstaged file that has been *renamed*  |
   +--------------+---+--------------+-----------------------------------------------+
   | |iconItFile| | / | |iconWtFile| | Staged/unstaged file which type has *changed* |
   +--------------+---+--------------+-----------------------------------------------+
   |              |   | |iconWuFile| | File that is *unreadable*                     |
   +--------------+---+--------------+-----------------------------------------------+
   |              |   | |iconGcFile| | File that has *conflicts*                     |
   +--------------+---+--------------+-----------------------------------------------+
   |              |   | |iconGiFile| | File that is *ignored*                        |
   +--------------+---+--------------+-----------------------------------------------+

.. |iconFile| image:: pics/file.png
   :class: icon
   :width: 24px

.. |iconIaFile| image:: pics/iaFile.png
   :class: icon
   :width: 24px

.. |iconIdFile| image:: pics/idFile.png
   :class: icon
   :width: 24px

.. |iconImFile| image:: pics/imFile.png
   :class: icon
   :width: 24px

.. |iconIrFile| image:: pics/irFile.png
   :class: icon
   :width: 24px

.. |iconItFile| image:: pics/itFile.png
   :class: icon
   :width: 24px

.. |iconWaFile| image:: pics/waFile.png
   :class: icon
   :width: 24px

.. |iconWdFile| image:: pics/wdFile.png
   :class: icon
   :width: 24px

.. |iconWmFile| image:: pics/wmFile.png
   :class: icon
   :width: 24px

.. |iconWrFile| image:: pics/wrFile.png
   :class: icon
   :width: 24px

.. |iconWtFile| image:: pics/wtFile.png
   :class: icon
   :width: 24px

.. |iconWuFile| image:: pics/wuFile.png
   :class: icon
   :width: 24px

.. |iconGcFile| image:: pics/gcFile.png
   :class: icon
   :width: 24px

.. |iconGiFile| image:: pics/giFile.png
   :class: icon
   :width: 24px

**Note:** you should always see the *unstaged* version of an icon.
The only case where you will see the *staged* version is if something went wrong during synchronisation.
Indeed, synchronisation is done using `Git <https://git-scm.com/>`__ and it may be that something caused it to fail (e.g., loss of Internet connection), in which case you will likely have to fix the problem yourself, using `Git <https://git-scm.com/>`__.
