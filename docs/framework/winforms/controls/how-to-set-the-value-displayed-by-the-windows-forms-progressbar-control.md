---
title: "Comment : définir la valeur affichée par le contrôle ProgressBar Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3fd66e10515e5135545f6fcfa64546141346519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="4a4dc-102">Comment : définir la valeur affichée par le contrôle ProgressBar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a4dc-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="4a4dc-103">Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4a4dc-104">Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] propose plusieurs méthodes pour afficher une valeur donnée dans le <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-104">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="4a4dc-105">Une approche que vous choisissez dépend de la tâche en cours ou le problème à résoudre.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="4a4dc-106">Le tableau suivant présente les approches que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="4a4dc-107">Approche</span><span class="sxs-lookup"><span data-stu-id="4a4dc-107">Approach</span></span>|<span data-ttu-id="4a4dc-108">Description</span><span class="sxs-lookup"><span data-stu-id="4a4dc-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4a4dc-109">Définir la valeur de la <xref:System.Windows.Forms.ProgressBar> contrôler directement.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="4a4dc-110">Cette approche est utile pour les tâches où vous connaissez le total d’éléments qui est impliqué, telles que la lecture des enregistrements à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="4a4dc-111">En outre, si vous devez uniquement définir la valeur une ou deux fois, cela est un moyen simple de le faire.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="4a4dc-112">Enfin, utilisez ce processus si vous avez besoin diminuer la valeur affichée par la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="4a4dc-113">Augmenter la <xref:System.Windows.Forms.ProgressBar> afficher par une valeur fixe.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="4a4dc-114">Cette approche est utile lorsque vous affichez un simple décompte entre le minimum et maximum, telles que le temps écoulé ou le nombre de fichiers qui ont été traitées sur un total connu.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="4a4dc-115">Augmenter la <xref:System.Windows.Forms.ProgressBar> afficher en une valeur variable.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="4a4dc-116">Cette approche est utile lorsque vous devez modifier la valeur affichée un nombre de fois dans une quantité différente.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="4a4dc-117">Par exemple lorsque vous souhaitez afficher la quantité d’espace disque consommé lors de l’écriture d’une série de fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="4a4dc-118">Le moyen le plus direct pour définir la valeur affichée par une barre de progression est en définissant le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="4a4dc-119">Cela est possible au moment du design ou au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="4a4dc-120">Pour définir la valeur du contrôle ProgressBar directement</span><span class="sxs-lookup"><span data-stu-id="4a4dc-120">To set the ProgressBar value directly</span></span>  
  
1.  <span data-ttu-id="4a4dc-121">Définir le <xref:System.Windows.Forms.ProgressBar> du contrôle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valeurs.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="4a4dc-122">Dans le code, définir du contrôle <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété à un entier compris entre les valeurs minimales et maximales que vous avez établi.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a4dc-123">Si vous définissez la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété à l’extérieur des limites établies par le <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriétés, le contrôle lève une <xref:System.ArgumentException> exception.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="4a4dc-124">L’exemple de code suivant illustre comment définir la <xref:System.Windows.Forms.ProgressBar> valeur directement.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="4a4dc-125">Le code lit les enregistrements d’une source de données et met à jour de la barre de progression et l’étiquette chaque fois qu’un enregistrement de données est en lecture.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="4a4dc-126">Cet exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Label> (contrôle), un <xref:System.Windows.Forms.ProgressBar> contrôle et une table de données avec une ligne nommée `CustomerRow` avec `FirstName` et `LastName` champs.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     Si vous affichez une progression qui procède à intervalle fixe, vous pouvez définir la valeur et puis appeler une méthode qui augmente la <xref:System.Windows.Forms.ProgressBar> valeur du contrôle de cet intervalle. <span data-ttu-id="4a4dc-128">Cela est utile pour les minuteries et autres scénarios où vous sont mesure pas la progression en pourcentage de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="4a4dc-129">Pour augmenter la barre de progression d’une valeur fixe</span><span class="sxs-lookup"><span data-stu-id="4a4dc-129">To increase the progress bar by a fixed value</span></span>  
  
1.  <span data-ttu-id="4a4dc-130">Définir le <xref:System.Windows.Forms.ProgressBar> du contrôle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valeurs.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="4a4dc-131">Définir le contrôle <xref:System.Windows.Forms.ProgressBar.Step%2A> valeur de propriété à un entier représentant la quantité pour augmenter la barre de progression affichée.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3.  <span data-ttu-id="4a4dc-132">Appelez le <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> méthode pour modifier la valeur affichée par la quantité définie le <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="4a4dc-133">L’exemple de code suivant illustre comment une barre de progression peut maintenir un nombre de fichiers dans une opération de copie.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="4a4dc-134">Dans l’exemple suivant, chaque fichier est lu en mémoire, la barre de progression et l’étiquette sont mis à jour pour refléter que le nombre total de fichiers en lecture.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="4a4dc-135">Cet exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Enfin, vous pouvez augmenter la valeur affichée par une barre de progression afin que chaque augmentation représente une quantité unique. <span data-ttu-id="4a4dc-137">Cela est utile lorsque vous assurez le suivi d’une série d’opérations uniques, telles que l’écriture de fichiers de tailles différentes sur un disque dur ou en mesurant les progrès sous forme de pourcentage de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="4a4dc-138">Pour augmenter la barre de progression d’une valeur dynamique</span><span class="sxs-lookup"><span data-stu-id="4a4dc-138">To increase the progress bar by a dynamic value</span></span>  
  
1.  <span data-ttu-id="4a4dc-139">Définir le <xref:System.Windows.Forms.ProgressBar> du contrôle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valeurs.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="4a4dc-140">Appelez le <xref:System.Windows.Forms.ProgressBar.Increment%2A> méthode pour modifier la valeur affichée par un entier que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="4a4dc-141">L’exemple de code suivant montre comment une barre de progression calcule la quantité d’espace disque a été utilisée au cours d’une opération de copie.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="4a4dc-142">Dans l’exemple suivant, chaque fichier est écrit sur le disque dur, la barre de progression et l’étiquette sont mis à jour pour refléter la quantité d’espace disque disponible.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="4a4dc-143">Cet exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4a4dc-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a4dc-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a4dc-144">See Also</span></span>  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [<span data-ttu-id="4a4dc-145">Vue d’ensemble du contrôle ProgressBar</span><span class="sxs-lookup"><span data-stu-id="4a4dc-145">ProgressBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="4a4dc-146">ProgressBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="4a4dc-146">ProgressBar Control</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
