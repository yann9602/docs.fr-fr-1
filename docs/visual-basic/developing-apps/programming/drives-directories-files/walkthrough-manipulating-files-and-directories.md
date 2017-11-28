---
title: "Manipulation de fichiers et de répertoires en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd1e61503394741e7943d30d383f2e7c5ea35f68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="4a969-102">Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a969-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="4a969-103">Cette procédure pas à pas présente les notions de base d’E/S de fichier dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a969-103">This walkthrough provides an introduction to the fundamentals of file I/O in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="4a969-104">Elle décrit comment créer une petite application qui répertorie et examine des fichiers texte dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a969-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="4a969-105">Pour chaque fichier texte sélectionné, l’application fournit des attributs de fichier et la première ligne de contenu.</span><span class="sxs-lookup"><span data-stu-id="4a969-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="4a969-106">Elle comprend une option pour écrire des informations dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="4a969-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="4a969-107">Cette procédure pas à pas utilise des membres de `My.Computer.FileSystem Object`, qui sont disponibles dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a969-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="4a969-108">Pour plus d'informations, voir <xref:Microsoft.VisualBasic.FileIO.FileSystem>.</span><span class="sxs-lookup"><span data-stu-id="4a969-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="4a969-109">À la fin de la procédure pas à pas, un exemple équivalent est fourni, qui utilise des classes de l’espace de noms <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="4a969-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="4a969-110">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="4a969-110">To create the project</span></span>  
  
1.  <span data-ttu-id="4a969-111">Dans le menu **Fichier**, cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="4a969-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="4a969-112">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="4a969-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="4a969-113">Dans le volet **Modèles installés**, développez **Visual Basic**, puis cliquez sur **Windows**.</span><span class="sxs-lookup"><span data-stu-id="4a969-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="4a969-114">Dans le volet **Modèles** du milieu, cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="4a969-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="4a969-115">Dans la zone **Nom**, tapez `FileExplorer` pour définir le nom de projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a969-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="4a969-116"> ajoute le projet à l’**Explorateur de solutions** et le Concepteur Windows Forms s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="4a969-116"> adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="4a969-117">Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.</span><span class="sxs-lookup"><span data-stu-id="4a969-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="4a969-118">Contrôle</span><span class="sxs-lookup"><span data-stu-id="4a969-118">Control</span></span>|<span data-ttu-id="4a969-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="4a969-119">Property</span></span>|<span data-ttu-id="4a969-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="4a969-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="4a969-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="4a969-121">**ListBox**</span></span>|<span data-ttu-id="4a969-122">**Nom**</span><span class="sxs-lookup"><span data-stu-id="4a969-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="4a969-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="4a969-123">**Button**</span></span>|<span data-ttu-id="4a969-124">**Nom**</span><span class="sxs-lookup"><span data-stu-id="4a969-124">**Name**</span></span><br /><br /> <span data-ttu-id="4a969-125">**Texte**</span><span class="sxs-lookup"><span data-stu-id="4a969-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="4a969-126">**Parcourir**</span><span class="sxs-lookup"><span data-stu-id="4a969-126">**Browse**</span></span>|  
    |<span data-ttu-id="4a969-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="4a969-127">**Button**</span></span>|<span data-ttu-id="4a969-128">**Nom**</span><span class="sxs-lookup"><span data-stu-id="4a969-128">**Name**</span></span><br /><br /> <span data-ttu-id="4a969-129">**Texte**</span><span class="sxs-lookup"><span data-stu-id="4a969-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="4a969-130">**Examiner**</span><span class="sxs-lookup"><span data-stu-id="4a969-130">**Examine**</span></span>|  
    |<span data-ttu-id="4a969-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="4a969-131">**CheckBox**</span></span>|<span data-ttu-id="4a969-132">**Nom**</span><span class="sxs-lookup"><span data-stu-id="4a969-132">**Name**</span></span><br /><br /> <span data-ttu-id="4a969-133">**Texte**</span><span class="sxs-lookup"><span data-stu-id="4a969-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="4a969-134">**Enregistrer les résultats**</span><span class="sxs-lookup"><span data-stu-id="4a969-134">**Save Results**</span></span>|  
    |<span data-ttu-id="4a969-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="4a969-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="4a969-136">**Nom**</span><span class="sxs-lookup"><span data-stu-id="4a969-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="4a969-137">Pour sélectionner un dossier et répertorier les fichiers dans un dossier</span><span class="sxs-lookup"><span data-stu-id="4a969-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="4a969-138">Créez un gestionnaire d’événements `Click` pour `browseButton` en double-cliquant sur le contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4a969-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="4a969-139">L'éditeur de code s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="4a969-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="4a969-140">Ajoutez le code ci-après au gestionnaire d'événements `Click`.</span><span class="sxs-lookup"><span data-stu-id="4a969-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     <span data-ttu-id="4a969-141">L’appel de `FolderBrowserDialog1.ShowDialog` ouvre la boîte de dialogue **Rechercher un dossier**.</span><span class="sxs-lookup"><span data-stu-id="4a969-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="4a969-142">Une fois que l’utilisateur a cliqué sur **OK**, la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> est envoyée en tant qu’argument à la méthode `ListFiles`, qui est ajoutée à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="4a969-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="4a969-143">Ajoutez la méthode `ListFiles` suivante.</span><span class="sxs-lookup"><span data-stu-id="4a969-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     <span data-ttu-id="4a969-144">Ce code efface d’abord le contrôle **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="4a969-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="4a969-145">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> récupère ensuite une collection de chaînes, une pour chaque fichier dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="4a969-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="4a969-146">La méthode `GetFiles` accepte un argument de modèle de recherche pour récupérer les fichiers qui correspondent à un modèle particulier.</span><span class="sxs-lookup"><span data-stu-id="4a969-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="4a969-147">Dans cet exemple, seuls les fichiers ayant l’extension .txt sont retournés.</span><span class="sxs-lookup"><span data-stu-id="4a969-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="4a969-148">Les chaînes qui sont retournées par la méthode `GetFiles` sont ensuite ajoutées à **ListBox**.</span><span class="sxs-lookup"><span data-stu-id="4a969-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="4a969-149">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="4a969-149">Run the application.</span></span> <span data-ttu-id="4a969-150">Cliquez sur le bouton **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="4a969-150">Click the **Browse** button.</span></span> <span data-ttu-id="4a969-151">Dans la boîte de dialogue **Rechercher un dossier**, accédez à un dossier qui contient des fichiers .txt, puis sélectionnez le dossier et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a969-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="4a969-152">`ListBox` contient une liste des fichiers.txt du dossier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="4a969-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="4a969-153">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="4a969-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="4a969-154">Pour obtenir les attributs d’un fichier et le contenu d’un fichier texte</span><span class="sxs-lookup"><span data-stu-id="4a969-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="4a969-155">Créez un gestionnaire d’événements `Click` pour `examineButton` en double-cliquant sur le contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4a969-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="4a969-156">Ajoutez le code ci-après au gestionnaire d'événements `Click`.</span><span class="sxs-lookup"><span data-stu-id="4a969-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     <span data-ttu-id="4a969-157">Le code vérifie qu’un élément est sélectionné dans le contrôle `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="4a969-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="4a969-158">Il obtient ensuite l’entrée du chemin du fichier à partir de `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="4a969-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="4a969-159">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> est utilisée pour vérifier si le fichier existe toujours.</span><span class="sxs-lookup"><span data-stu-id="4a969-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="4a969-160">Le chemin du fichier est envoyé en tant qu’argument à la méthode `GetTextForOutput`, qui est ajoutée à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="4a969-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="4a969-161">Cette méthode retourne une chaîne qui contient des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="4a969-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="4a969-162">Les informations sur le fichier s’affichent dans un élément **MessageBox**.</span><span class="sxs-lookup"><span data-stu-id="4a969-162">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="4a969-163">Ajoutez la méthode `GetTextForOutput` suivante.</span><span class="sxs-lookup"><span data-stu-id="4a969-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     <span data-ttu-id="4a969-164">Le code utilise la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> pour obtenir des paramètres de fichier.</span><span class="sxs-lookup"><span data-stu-id="4a969-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="4a969-165">Les paramètres de fichier sont ajoutés à un <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="4a969-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="4a969-166">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lit le contenu du fichier dans un <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="4a969-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="4a969-167">La première ligne du contenu est obtenue à partir du `StreamReader` et est ajoutée au `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="4a969-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="4a969-168">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="4a969-168">Run the application.</span></span> <span data-ttu-id="4a969-169">Cliquez sur **Parcourir** et recherchez un dossier qui contient des fichiers .txt.</span><span class="sxs-lookup"><span data-stu-id="4a969-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="4a969-170">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a969-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="4a969-171">Sélectionnez un fichier dans le contrôle `ListBox`, puis cliquez sur **Examiner**.</span><span class="sxs-lookup"><span data-stu-id="4a969-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="4a969-172">`MessageBox` affiche les informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="4a969-172">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="4a969-173">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="4a969-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="4a969-174">Pour ajouter une entrée de journal</span><span class="sxs-lookup"><span data-stu-id="4a969-174">To add a log entry</span></span>  
  
1.  <span data-ttu-id="4a969-175">Ajoutez le code suivant à la fin du gestionnaire d’événements `examineButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4a969-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     <span data-ttu-id="4a969-176">Le code définit le chemin du fichier journal de sorte que ce dernier soit placé dans le même répertoire que celui du fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="4a969-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="4a969-177">Le texte de l’entrée de journal prend comme valeur la date et l’heure actuelles, suivies des informations sur le fichier.</span><span class="sxs-lookup"><span data-stu-id="4a969-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="4a969-178">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, avec l’argument `append` défini sur `True`, est utilisée pour créer l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="4a969-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="4a969-179">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="4a969-179">Run the application.</span></span> <span data-ttu-id="4a969-180">Accédez à un fichier texte, sélectionnez-le dans le contrôle `ListBox`, cochez la case **Enregistrer les résultats**, puis cliquez sur **Examiner**.</span><span class="sxs-lookup"><span data-stu-id="4a969-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="4a969-181">Vérifiez que l’entrée de journal est écrite dans le fichier `log.txt`.</span><span class="sxs-lookup"><span data-stu-id="4a969-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="4a969-182">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="4a969-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="4a969-183">Pour utiliser le répertoire actif</span><span class="sxs-lookup"><span data-stu-id="4a969-183">To use the current directory</span></span>  
  
1.  <span data-ttu-id="4a969-184">Créez un gestionnaire d’événements pour `Form1_Load` en double-cliquant sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4a969-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="4a969-185">Ajoutez le code suivant au gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="4a969-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     <span data-ttu-id="4a969-186">Ce code définit le répertoire actif comme le répertoire par défaut de l’Explorateur de dossiers.</span><span class="sxs-lookup"><span data-stu-id="4a969-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="4a969-187">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="4a969-187">Run the application.</span></span> <span data-ttu-id="4a969-188">Quand vous cliquez pour la première fois sur **Parcourir**, la boîte de dialogue **Rechercher un dossier** affiche le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="4a969-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="4a969-189">Arrêtez l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="4a969-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="4a969-190">Pour activer des contrôles de manière sélective</span><span class="sxs-lookup"><span data-stu-id="4a969-190">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="4a969-191">Ajoutez la méthode `SetEnabled` suivante.</span><span class="sxs-lookup"><span data-stu-id="4a969-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     <span data-ttu-id="4a969-192">La méthode `SetEnabled` active ou désactive les contrôles, selon qu’un élément est sélectionné ou non dans le contrôle `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="4a969-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="4a969-193">Créez un gestionnaire d’événements `SelectedIndexChanged` pour `filesListBox` en double-cliquant sur le contrôle `ListBox` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="4a969-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="4a969-194">Ajoutez un appel à `SetEnabled` dans le nouveau gestionnaire d’événements `filesListBox_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="4a969-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="4a969-195">Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `browseButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4a969-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="4a969-196">Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `Form1_Load`.</span><span class="sxs-lookup"><span data-stu-id="4a969-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="4a969-197">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="4a969-197">Run the application.</span></span> <span data-ttu-id="4a969-198">La case **Enregistrer les résultats** et le bouton **Examiner** sont désactivés si aucun élément n’est sélectionné dans le contrôle `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="4a969-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="4a969-199">Exemple complet de l’utilisation de My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="4a969-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="4a969-200">L’exemple complet se trouve ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4a969-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="4a969-201">Exemple complet de l’utilisation de System.IO</span><span class="sxs-lookup"><span data-stu-id="4a969-201">Full example using System.IO</span></span>  
 <span data-ttu-id="4a969-202">L’exemple équivalent suivant utilise des classes de l’espace de noms <xref:System.IO> au lieu d’utiliser des objets `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="4a969-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a969-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a969-203">See Also</span></span>  
 <xref:System.IO>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>  
 [<span data-ttu-id="4a969-204">Procédure pas à pas : manipulation de fichiers à l’aide de méthodes du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4a969-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
