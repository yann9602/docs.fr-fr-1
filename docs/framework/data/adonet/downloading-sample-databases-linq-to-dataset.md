---
title: "T&#233;l&#233;chargement d&#39;exemples de base de donn&#233;es (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# T&#233;l&#233;chargement d&#39;exemples de base de donn&#233;es (LINQ to DataSet)
Les exemples et procédures pas à pas de la documentation [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sont tirés de l'exemple de base de données AdventureWorks.  Vous pouvez télécharger ce produit gratuitement à partir du site de téléchargement Microsoft. Les exemples et procédures pas à pas de la documentation [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] utilisent SQL Server comme magasin de données.  SQL Server Express Edition, disponible gratuitement, peut également être utilisé comme magasin de données à la place de SQL Server.  
  
## Téléchargement et installation de la base de données AdventureWorks  
  
#### Pour télécharger et installer l'exemple de base de données AdventureWorks pour SQL Server  
  
1.  Ouvrez Internet Explorer.  
  
2.  Accédez au site web [Exemples et exemples de bases de données SQL Server 2005](http://go.microsoft.com/fwlink/?linkid=31046).  
  
3.  Suivez les instructions pour télécharger l'exemple de base de données AdventureWorks pour votre type de processeur \(AdventureWorksDB.msi par exemple\), et enregistrez le fichier .MSI sur votre ordinateur local.  
  
4.  Si vous disposez d'une version précédente de la base de données AdventureWorks installée à partir du téléchargement ou pendant la configuration de SQL Server, vous devez la supprimer avant d'exécuter AdventureWorks.msi.  
  
#### Pour supprimer un téléchargement précédent d'un exemple de base de données AdventureWorks  
  
1.  Supprimez la base de données AdventureWorks ou AdventureWorksDW.  
  
2.  Dans **Ajout\/Suppression de programmes**, sélectionnez **AdventureWorksDB** ou **AdventureWorksBI**, puis cliquez sur **Supprimer**.  
  
#### Pour supprimer un exemple de base de données AdventureWorks précédemment installé à l'aide du programme d'installation  
  
1.  Supprimez la base de données AdventureWorks ou AdventureWorksDW.  
  
2.  Dans **Ajout\/Suppression de programmes**, sélectionnez **Microsoft SQL Server 2005**, puis cliquez sur **Modifier**.  
  
3.  Dans **Sélection du composant**, sélectionnez **Composants de la station de travail**, puis cliquez sur **Suivant**.  
  
4.  Dans l'écran **Assistant Installation de SQL Server**, cliquez sur **Suivant**.  
  
5.  À partir d'**Analyse de la configuration système**, cliquez sur **Suivant**.  
  
6.  Dans **Changer ou supprimer l'instance**, cliquez sur **Modifier les composants installés**.  
  
7.  Dans **Sélection de composant**, développez le nœud **Documentation, exemples et exemples de bases de données**.  
  
8.  Sélectionnez **Exemples de code et d'applications**.  Développez **Exemples de bases de données**, sélectionnez l'exemple de base de données à supprimer, puis sélectionnez **Ce composant ne sera non disponible**.  Cliquez sur **Suivant**.  
  
9. Cliquez sur **Installer** et terminez l'Assistant Installation.  
  
#### Pour attacher les fichiers de l'exemple de base de données AdventureWorks à une instance de SQL Server  
  
1.  Une fois le téléchargement du fichier de programme d'installation de l'exemple de base de données terminé, double\-cliquez sur le fichier **AdventureWorksDB.msi** \(ou sur le fichier que vous avez téléchargé\) pour installer la base de données.  Par défaut, la base de données est installée dans c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data.  
  
2.  Attachez les fichiers de la base de données AdventureWorks à une instance de SQL Server en exécutant le script suivant à l'aide de SQLCMD ou SQL Server Management Studio :  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     Si vous avez installé ces fichiers dans un lecteur ou un répertoire différent, vous devez modifier les chemins en conséquence avant d'exécuter la procédure stockée `sp_attach_db`.  
  
## Téléchargement de SQL Server Express Edition  
 Les exemples et procédures pas à pas de la section [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] utilisent SQL Server 2005 comme magasin de données, mais peuvent être modifiés pour utiliser SQL Server Express Edition à la place.  SQL Server Express Edition est disponible gratuitement et vous pouvez le redistribuer avec les applications.  Si vous utilisez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition est inclus dans les éditions professionnelles et ultérieures.  
  
#### Pour télécharger et installer SQL Server Express Edition  
  
1.  Démarrez Internet Explorer.  
  
2.  Accédez à la page de téléchargement  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070).  
  
3.  Suivez les instructions d'installation indiquées sur le site Web.  
  
## Voir aussi  
 [Mise en route](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)