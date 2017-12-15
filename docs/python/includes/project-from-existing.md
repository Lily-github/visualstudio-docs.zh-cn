1. 启动 Visual Studio，然后选择“文件”>“新建”>“项目”。

1. 在“新建项目”对话框中，搜索“Python”，选择“从现有的 Python 代码”模板，为项目提供名称和位置，然后选择“确定”。

1. 在出现的向导中，设置现有代码的路径，设置文件类型筛选器，并指定项目需要的任何搜索路径，然后选择“下一步”。 如果你不知道搜索路径是什么，则将该字段留空。

    ![根据现有代码新建项目，步骤 1](../media/projects-from-existing-1.png)

1. 在下一个对话框中，选择项目的启动文件，然后选择“下一步”。 （如果需要，选择一个环境；否则接受默认设置。）请注意，对话框仅显示根文件夹中的文件；如果所需的文件在子文件夹中，请将启动文件保留为空，稍后在解决方案资源管理器中进行设置（如下所述）。 

    ![根据现有代码新建项目，步骤 2](../media/projects-from-existing-2.png)

1. 选择要在其中保存项目文件（磁盘上的 `.pyproj` 文件）的位置。 如果适用，还可以包括虚拟环境的自动检测以及针对不同 Web 框架自定义项目。 如果不确定这些选项，请保持它们设置为默认值。

    ![根据现有代码新建项目，步骤 3](../media/projects-from-existing-3.png)

1.  选择“完成”，Visual Studio 将创建项目并在解决方案资源管理器中打开该项目。 若要将.`.pyproj` 文件移动到其他位置，请在解决方案资源管理器中选中它，并选择“文件”>“另存为”。 此操作更新项目中的文件引用，但不移动任何代码文件。

1. 若要设置不同的启动文件，请在解决方案资源管理器中找到该文件，右键单击，然后选择“设置为启动文件”。