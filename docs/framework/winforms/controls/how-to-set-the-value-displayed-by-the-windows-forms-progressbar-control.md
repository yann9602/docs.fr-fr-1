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
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Comment : définir la valeur affichée par le contrôle ProgressBar Windows Forms
> [!IMPORTANT]
>  Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] propose plusieurs méthodes pour afficher une valeur donnée dans le <xref:System.Windows.Forms.ProgressBar> contrôle. Une approche que vous choisissez dépend de la tâche en cours ou le problème à résoudre. Le tableau suivant présente les approches que vous pouvez choisir.  
  
|Approche|Description|  
|--------------|-----------------|  
|Définir la valeur de la <xref:System.Windows.Forms.ProgressBar> contrôler directement.|Cette approche est utile pour les tâches où vous connaissez le total d’éléments qui est impliqué, telles que la lecture des enregistrements à partir d’une source de données. En outre, si vous devez uniquement définir la valeur une ou deux fois, cela est un moyen simple de le faire. Enfin, utilisez ce processus si vous avez besoin diminuer la valeur affichée par la barre de progression.|  
|Augmenter la <xref:System.Windows.Forms.ProgressBar> afficher par une valeur fixe.|Cette approche est utile lorsque vous affichez un simple décompte entre le minimum et maximum, telles que le temps écoulé ou le nombre de fichiers qui ont été traitées sur un total connu.|  
|Augmenter la <xref:System.Windows.Forms.ProgressBar> afficher en une valeur variable.|Cette approche est utile lorsque vous devez modifier la valeur affichée un nombre de fois dans une quantité différente. Par exemple lorsque vous souhaitez afficher la quantité d’espace disque consommé lors de l’écriture d’une série de fichiers sur le disque.|  
  
 Le moyen le plus direct pour définir la valeur affichée par une barre de progression est en définissant le <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété. Cela est possible au moment du design ou au moment de l’exécution.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Pour définir la valeur du contrôle ProgressBar directement  
  
1.  Définir le <xref:System.Windows.Forms.ProgressBar> du contrôle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valeurs.  
  
2.  Dans le code, définir du contrôle <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété à un entier compris entre les valeurs minimales et maximales que vous avez établi.  
  
    > [!NOTE]
    >  Si vous définissez la <xref:System.Windows.Forms.ProgressBar.Value%2A> propriété à l’extérieur des limites établies par le <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriétés, le contrôle lève une <xref:System.ArgumentException> exception.  
  
     L’exemple de code suivant illustre comment définir la <xref:System.Windows.Forms.ProgressBar> valeur directement. Le code lit les enregistrements d’une source de données et met à jour de la barre de progression et l’étiquette chaque fois qu’un enregistrement de données est en lecture. Cet exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Label> (contrôle), un <xref:System.Windows.Forms.ProgressBar> contrôle et une table de données avec une ligne nommée `CustomerRow` avec `FirstName` et `LastName` champs.  
  
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
  
     Si vous affichez une progression qui procède à intervalle fixe, vous pouvez définir la valeur et puis appeler une méthode qui augmente la <xref:System.Windows.Forms.ProgressBar> valeur du contrôle de cet intervalle. Cela est utile pour les minuteries et autres scénarios où vous sont mesure pas la progression en pourcentage de l’ensemble.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Pour augmenter la barre de progression d’une valeur fixe  
  
1.  Définir le <xref:System.Windows.Forms.ProgressBar> du contrôle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valeurs.  
  
2.  Définir le contrôle <xref:System.Windows.Forms.ProgressBar.Step%2A> valeur de propriété à un entier représentant la quantité pour augmenter la barre de progression affichée.  
  
3.  Appelez le <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> méthode pour modifier la valeur affichée par la quantité définie le <xref:System.Windows.Forms.ProgressBar.Step%2A> propriété.  
  
     L’exemple de code suivant illustre comment une barre de progression peut maintenir un nombre de fichiers dans une opération de copie.  
  
     Dans l’exemple suivant, chaque fichier est lu en mémoire, la barre de progression et l’étiquette sont mis à jour pour refléter que le nombre total de fichiers en lecture. Cet exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.  
  
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
  
     Enfin, vous pouvez augmenter la valeur affichée par une barre de progression afin que chaque augmentation représente une quantité unique. Cela est utile lorsque vous assurez le suivi d’une série d’opérations uniques, telles que l’écriture de fichiers de tailles différentes sur un disque dur ou en mesurant les progrès sous forme de pourcentage de l’ensemble.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Pour augmenter la barre de progression d’une valeur dynamique  
  
1.  Définir le <xref:System.Windows.Forms.ProgressBar> du contrôle <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> valeurs.  
  
2.  Appelez le <xref:System.Windows.Forms.ProgressBar.Increment%2A> méthode pour modifier la valeur affichée par un entier que vous spécifiez.  
  
     L’exemple de code suivant montre comment une barre de progression calcule la quantité d’espace disque a été utilisée au cours d’une opération de copie.  
  
     Dans l’exemple suivant, chaque fichier est écrit sur le disque dur, la barre de progression et l’étiquette sont mis à jour pour refléter la quantité d’espace disque disponible. Cet exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Label> contrôle et un <xref:System.Windows.Forms.ProgressBar> contrôle.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [Vue d’ensemble du contrôle ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [ProgressBar, contrôle](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
