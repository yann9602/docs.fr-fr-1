---
title: "Comment&#160;: d&#233;finir la valeur affich&#233;e par le contr&#244;le ProgressBar Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Increment (méthode)"
  - "PerformStep (méthode)"
  - "Progress (contrôles), définir la valeur affichée"
  - "ProgressBar (contrôle Windows Forms), définir la valeur affichée"
  - "Step (propriété)"
  - "Value (propriété)"
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;finir la valeur affich&#233;e par le contr&#244;le ProgressBar Windows Forms
> [!IMPORTANT]
>  Le contrôle <xref:System.Windows.Forms.ToolStripProgressBar> remplace le contrôle <xref:System.Windows.Forms.ProgressBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ProgressBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] propose plusieurs méthodes pour afficher une valeur donnée dans le contrôle <xref:System.Windows.Forms.ProgressBar>.  Le choix de l'approche dépend de la tâche à exécuter ou du problème à résoudre.  Le tableau suivant affiche les approches que vous pouvez choisir.  
  
|Approche|Description|  
|--------------|-----------------|  
|Définir la valeur du contrôle <xref:System.Windows.Forms.ProgressBar> directement.|Cette approche est utile pour les tâches où vous connaissez le nombre total d'éléments à analyser, comme la lecture d'enregistrements à partir d'une source de données.  De plus, elle est particulièrement adaptée lorsque vous ne devez définir la valeur qu'une ou deux fois.  Utilisez également ce processus si vous devez diminuer la valeur affichée par la barre de progression.|  
|Augmenter la valeur affichée par le contrôle <xref:System.Windows.Forms.ProgressBar> d'une valeur fixe.|Cette approche est utile lorsque vous affichez un simple décompte compris entre un minimum et un maximum, comme le temps écoulé ou le nombre de fichiers traités sur un nombre total donné.|  
|Augmenter la valeur affichée par le contrôle <xref:System.Windows.Forms.ProgressBar> d'une valeur variable.|Cette approche est utile lorsque vous devez modifier la valeur affichée un certain nombre de fois et à l'aide d'incréments différents.  C'est le cas, par exemple, lorsque vous souhaitez afficher la quantité d'espace disque en cours d'utilisation pendant l'écriture d'une série de fichiers.|  
  
 La façon la plus directe de définir la valeur affichée par une barre de progression consiste à définir la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A>.  Vous pouvez le faire au moment du design ou de l'exécution.  
  
### Pour définir la valeur du contrôle ProgressBar directement  
  
1.  Définissez les valeurs <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> du contrôle <xref:System.Windows.Forms.ProgressBar>.  
  
2.  Dans le code, affectez à la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> du contrôle une valeur entière comprise entre les valeurs minimale et maximale que vous avez établies.  
  
    > [!NOTE]
    >  Si vous définissez la propriété <xref:System.Windows.Forms.ProgressBar.Value%2A> à l'extérieur des limites établies par les propriétés <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A>, le contrôle lève une exception <xref:System.ArgumentException>.  
  
     L'exemple de code ci\-dessous montre comment définir la valeur du contrôle <xref:System.Windows.Forms.ProgressBar> directement.  Le code lit les enregistrements d'une source de données, met à jour la barre de progression et l'étiquette à chaque lecture d'un enregistrement.  Cet exemple suppose que votre formulaire contient deux contrôles, <xref:System.Windows.Forms.Label> et <xref:System.Windows.Forms.ProgressBar>, et une table de données avec une ligne nommée `CustomerRow`  incluant les champs `FirstName`  et `Last Name` .  
  
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
  
     Si vous affichez une progression qui procède à intervalle fixe, vous pouvez définir la valeur, puis appeler une méthode qui augmente la valeur du contrôle <xref:System.Windows.Forms.ProgressBar> de cet intervalle.  Cette procédure est utile pour les minuteries et autres scénarios où vous ne mesurez pas une progression en tant que pourcentage d'un ensemble.  
  
### Pour augmenter la barre de progression d'une valeur fixe  
  
1.  Définissez les valeurs <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> du contrôle <xref:System.Windows.Forms.ProgressBar>.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.ProgressBar.Step%2A> du contrôle un nombre entier représentant la quantité en fonction de laquelle la valeur affichée par la barre de progression doit être augmentée.  
  
3.  Appelez la méthode <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> pour remplacer la valeur affichée en fonction de la quantité définie dans la propriété <xref:System.Windows.Forms.ProgressBar.Step%2A>.  
  
     L'exemple de code ci\-dessous montre comment une barre de progression tient à jour un compte des fichiers dans une opération de copie.  
  
     Comme chaque fichier est lu dans la mémoire, la barre de progression et l'étiquette sont mises à jour pour refléter le nombre total de fichiers lus.  Cet exemple suppose que votre formulaire contient deux contrôles, <xref:System.Windows.Forms.Label> et <xref:System.Windows.Forms.ProgressBar>.  
  
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
  
     Enfin, vous pouvez augmenter la valeur affichée par une barre de progression de sorte que chaque augmentation représente une quantité unique.  Cette procédure est utile lorsque vous assurez le suivi d'une série d'opérations uniques, comme l'écriture de fichiers de tailles différentes sur un disque dur ou l'évaluation de la progression d'une tâche en tant que pourcentage d'un ensemble.  
  
### Pour augmenter la barre de progression d'une valeur dynamique  
  
1.  Définissez les valeurs <xref:System.Windows.Forms.ProgressBar.Minimum%2A> et <xref:System.Windows.Forms.ProgressBar.Maximum%2A> du contrôle <xref:System.Windows.Forms.ProgressBar>.  
  
2.  Appelez la méthode <xref:System.Windows.Forms.ProgressBar.Increment%2A> pour remplacer la valeur affichée par un entier que vous spécifiez.  
  
     L'exemple de code ci\-dessous montre comment une barre de progression calcule la quantité d'espace disque utilisée pendant une opération de copie.  
  
     Dans cet exemple, comme chaque fichier est écrit sur le disque dur, la barre de progression et l'étiquette sont mises à jour pour refléter la quantité d'espace disque disponible.  Cet exemple suppose que votre formulaire contient deux contrôles, <xref:System.Windows.Forms.Label> et <xref:System.Windows.Forms.ProgressBar>.  
  
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
  
## Voir aussi  
 <xref:System.Windows.Forms.ProgressBar>   
 <xref:System.Windows.Forms.ToolStripProgressBar>   
 [Vue d'ensemble du contrôle ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)   
 [ProgressBar, contrôle](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)