---
title: "Collections de sch&#233;mas SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Collections de sch&#233;mas SQL Server
Le fournisseur de données Microsoft .NET Framework pour SQL Server prend en charge d'autres collections de schémas en plus des collections de schémas courantes.  Les collections de schémas varient légèrement selon la version de SQL Server que vous utilisez.  Pour établir la liste des collections de schémas prises en charge, appelez la méthode **GetSchema** sans argument ou avec le nom de collection de schémas « MetaDataCollections ».  Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu'elles prennent en charge et le nombre d'éléments d'identification qu'elles utilisent.  
  
## Bases de données  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|database\_name|Chaîne|Nom de la base de données.|  
|Dbid|Int16|ID de la base de données.|  
|create\_date|DateTime|Date de création de la base de données.|  
  
## Clés étrangères  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|constraint\_catalog|Chaîne|Catalogue auquel la contrainte appartient.|  
|constraint\_schema|Chaîne|Schéma contenant la contrainte.|  
|constraint\_name|Chaîne|Nom.|  
|table\_catalog|Chaîne|Nom de la table dont la contrainte fait partie.|  
|table\_schema|Chaîne|Schéma contenant la table.|  
|table\_name|Chaîne|Nom de la table|  
|constraint\_type|Chaîne|Type de contrainte.  Seul « FOREIGN KEY » est autorisé.|  
|is\_deferrable|Chaîne|Indique si la contrainte peut être différée.  Retourne NO.|  
|initially\_deferred|Chaîne|Indique si la contrainte est initialement différée.  Retourne NO.|  
  
## Index  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|constraint\_catalog|Chaîne|Catalogue auquel l'index appartient.|  
|constraint\_schema|Chaîne|Schéma contenant l'index.|  
|constraint\_name|Chaîne|Nom de l'index.|  
|table\_catalog|Chaîne|Nom de la table auquel l'index est associé.|  
|table\_schema|Chaîne|Schéma contenant la table à laquelle l'index est associé.|  
|table\_name|Chaîne|Nom de table.|  
  
### Indexes \(SQL Server 2008\)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, les colonnes suivantes sont été ajoutées à la collection de schémas Indexes afin de prendre en charge de nouveaux types de données spatiales, flux de fichiers et colonnes fragmentées.  Ces colonnes ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|type\_desc|Chaîne|Le type de l'index est l'un des suivants :<br /><br /> -   HEAP<br />-   CLUSTERED<br />-   NONCLUSTERED<br />-   XML<br />-   SPATIAL|  
  
## IndexColumns  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|constraint\_catalog|Chaîne|Catalogue auquel l'index appartient.|  
|constraint\_schema|Chaîne|Schéma contenant l'index.|  
|constraint\_name|Chaîne|Nom de l'index.|  
|table\_catalog|Chaîne|Nom de la table auquel l'index est associé.|  
|table\_schema|Chaîne|Schéma contenant la table à laquelle l'index est associé.|  
|table\_name|Chaîne|Nom de table.|  
|column\_name|Chaîne|Nom de la colonne à laquelle l'index est associé.|  
|ordinal\_position|Int32|Position du numéro de colonne.|  
|KeyType|UInt16|Type d'objet.|  
  
## Procédures  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|specific\_catalog|Chaîne|Nom spécifique du catalogue.|  
|specific\_schema|Chaîne|Nom spécifique du schéma.|  
|specific\_name|Chaîne|Nom spécifique du catalogue.|  
|routine\_catalog|Chaîne|Catalogue auquel appartient la procédure stockée.|  
|routine\_schema|Chaîne|Schéma contenant la procédure stockée.|  
|routine\_name|Chaîne|Nom de la procédure stockée.|  
|routine\_type|Chaîne|Retourne PROCEDURE pour les procédures stockées et FUNCTION pour les fonctions.|  
|created|DateTime|Heure à laquelle la procédure a été créée.|  
|last\_altered|DateTime|Heure à laquelle la procédure a été modifiée pour la dernière fois.|  
  
## Paramètres de procédure  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|specific\_catalog|Chaîne|Nom du catalogue de la procédure pour laquelle ceci est un paramètre.|  
|specific\_schema|Chaîne|Schéma contenant la procédure dont ce paramètre fait partie.|  
|specific\_name|Chaîne|Nom de la procédure dont ce paramètre fait partie.|  
|ordinal\_position|Int16|Position ordinale du paramètre commençant à 1.  Pour la valeur de retour d'une procédure, cela donne 0.|  
|parameter\_mode|Chaîne|Retourne IN pour un paramètre d'entrée, OUT pour un paramètre de sortie et INOUT pour un paramètre d'entrée\/sortie.|  
|is\_result|Chaîne|Retourne YES s'il indique que le résultat de la procédure est une fonction.  Sinon, retourne NO.|  
|as\_locator|Chaîne|Retourne YES s'il est déclaré comme pointeur.  Sinon, retourne NO.|  
|parameter\_name|Chaîne|Nom du paramètre.  NULL si ceci correspond à la valeur de retour d'une fonction.|  
|data\_type|Chaîne|Type de données fourni par le système.|  
|character\_maximum\_length|Int32|Longueur maximale en caractères pour des types de données binaires ou sous forme de caractères.  Sinon, retourne NULL.|  
|character\_octet\_length|Int32|Longueur maximale en octets pour des types de données binaires ou sous forme de caractères.  Sinon, retourne NULL.|  
|collation\_catalog|Chaîne|Nom de catalogue du classement du paramètre.  S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|collation\_schema|Chaîne|Retourne toujours NULL.|  
|collation\_name|Chaîne|Nom du classement du paramètre.  S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|character\_set\_catalog|Chaîne|Nom de catalogue de l'ensemble de caractères du paramètre.  S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|character\_set\_schema|Chaîne|Retourne toujours NULL.|  
|character\_set\_name|Chaîne|Nom du jeu de caractères du paramètre.  S'il ne s'agit pas de l'un des types de caractère, retourne NULL.|  
|numeric\_precision|Byte|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, retourne NULL.|  
|numeric\_precision\_radix|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, retourne NULL.|  
|numeric\_scale|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, retourne NULL.|  
|datetime\_precision|Int16|Précision en secondes fractionnelles si le type de paramètre est datetime ou smalldatetime.  Sinon, retourne NULL.|  
|interval\_type|Chaîne|NULL.  Réservé pour un usage futur de SQL Server.|  
|interval\_precision|Int16|NULL.  Réservé pour un usage futur de SQL Server.|  
  
## Tables  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|table\_catalog|Chaîne|Catalogue de la table.|  
|table\_schema|Chaîne|Schéma contenant la table.|  
|table\_name|Chaîne|Nom de la table.|  
|table\_type|Chaîne|Type de table.  Peut être VIEW ou BASE TABLE.|  
  
## Columns  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|table\_catalog|Chaîne|Catalogue de la table.|  
|table\_schema|Chaîne|Schéma contenant la table.|  
|table\_name|Chaîne|Nom de la table.|  
|column\_name|Chaîne|Nom de la colonne.|  
|ordinal\_position|Int16|Numéro d'identification de colonne.|  
|column\_default|Chaîne|Valeur par défaut de la colonne|  
|is\_nullable|Chaîne|Prise en charge des valeurs null dans la colonne.  Si cette colonne autorise les valeurs NULL, elle retourne YES.  Dans le cas contraire, elle retourne No.|  
|data\_type|Chaîne|Type de données fourni par le système.|  
|character\_maximum\_length|Int32 – Sql8, Int16 – Sql7|Longueur maximale en caractères pour les données binaires, sous forme de caractères, de texte ou d'image.  Sinon, la valeur NULL est retournée.|  
|character\_octet\_length|Int32 – SQL8, Int16 – Sql7|Longueur maximale en octets pour les données binaires, sous forme de caractères, de texte ou d'image.  Sinon, la valeur NULL est retournée.|  
|numeric\_precision|Octet non signé|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|numeric\_precision\_radix|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|numeric\_scale|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|datetime\_precision|Int16|Code Subtype pour les types de données d'intervalle datetime et SQL\-92.  Pour les autres types de données, la valeur NULL est retournée.|  
|character\_set\_catalog|Chaîne|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte.  Sinon, la valeur NULL est retournée.|  
|character\_set\_schema|Chaîne|Retourne toujours NULL.|  
|character\_set\_name|Chaîne|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte.  Sinon, la valeur NULL est retournée.|  
|collation\_catalog|Chaîne|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte.  Sinon, cette colonne a une valeur NULL.|  
  
### Columns \(SQL Server 2008\)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, les colonnes suivantes sont été ajoutées à la collection de schémas Columns afin de prendre en charge de nouveaux types de données spatiales, flux de fichiers et colonnes fragmentées.  Ces colonnes ne sont pas prises en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|IS\_FILESTREAM|Chaîne|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS\_SPARSE|Chaîne|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS\_COLUMN\_SET|Chaîne|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
### AllColumns \(SQL Server 2008\)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, la collection de schémas AllColumns a été ajoutée afin de permettre la prise en charge des colonnes fragmentées.  AllColumns n'est pas prise en charge dans les versions précédentes de .NET Framework et SQL Server.  
  
 AllColumns présente les mêmes restrictions et schéma DataTable résultant que la collection de schémas Columns.  La seule différence vient du fait que la collection AllColumns inclut des colonnes d'ensembles de colonnes qui ne sont pas incluses dans la collection de schémas Columns.  Le tableau suivant décrit ces colonnes.  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|table\_catalog|Chaîne|Catalogue de la table.|  
|table\_schema|Chaîne|Schéma contenant la table.|  
|table\_name|Chaîne|Nom de la table.|  
|column\_name|Chaîne|Nom de la colonne.|  
|ordinal\_position|Int16|Numéro d'identification de colonne.|  
|column\_default|Chaîne|Valeur par défaut de la colonne|  
|is\_nullable|Chaîne|Prise en charge des valeurs null dans la colonne.  Si cette colonne autorise les valeurs NULL, elle retourne YES.  Dans le cas contraire, elle retourne NO.|  
|data\_type|Chaîne|Type de données fourni par le système.|  
|character\_maximum\_length|Int32|Longueur maximale en caractères pour les données binaires, sous forme de caractères, de texte ou d'image.  Sinon, la valeur NULL est retournée.|  
|character\_octet\_length|Int32|Longueur maximale en octets pour les données binaires, sous forme de caractères, de texte ou d'image.  Sinon, la valeur NULL est retournée.|  
|numeric\_precision|Octet non signé|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|numeric\_precision\_radix|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|numeric\_scale|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|datetime\_precision|Int16|Code Subtype pour les types de données d'intervalle datetime et SQL\-92.  Pour les autres types de données, la valeur NULL est retournée.|  
|character\_set\_catalog|Chaîne|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte.  Sinon, la valeur NULL est retournée.|  
|character\_set\_schema|Chaîne|Retourne toujours NULL.|  
|character\_set\_name|Chaîne|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte.  Sinon, la valeur NULL est retournée.|  
|collation\_catalog|Chaîne|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte.  Sinon, cette colonne a une valeur NULL.|  
|IS\_FILESTREAM|Chaîne|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS\_SPARSE|Chaîne|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS\_COLUMN\_SET|Chaîne|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
### ColumnSetColumns \(SQL Server 2008\)  
 Depuis .NET Framework version 3.5 SP1 et SQL Server 2008, la collection de schémas ColumnSetColumns a été ajoutée afin de permettre la prise en charge des colonnes fragmentées.  ColumnSetColumns n'est pas prise en charge dans les versions précédentes de .NET Framework et SQL Server.  La collection de schémas ColumnSetColumns retourne le schéma de toutes les colonnes dans un ensemble de colonnes.  Le tableau suivant décrit ces colonnes.  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|table\_catalog|Chaîne|Catalogue de la table.|  
|table\_schema|Chaîne|Schéma contenant la table.|  
|table\_name|Chaîne|Nom de la table.|  
|column\_name|Chaîne|Nom de la colonne.|  
|ordinal\_position|Int16|Numéro d'identification de colonne.|  
|column\_default|Chaîne|Valeur par défaut de la colonne|  
|is\_nullable|Chaîne|Prise en charge des valeurs null dans la colonne.  Si cette colonne autorise les valeurs NULL, elle retourne YES.  Dans le cas contraire, elle retourne NO.|  
|data\_type|Chaîne|Type de données fourni par le système.|  
|character\_maximum\_length|Int32|Longueur maximale en caractères pour les données binaires, sous forme de caractères, de texte ou d'image.  Sinon, la valeur NULL est retournée.|  
|character\_octet\_length|Int32|Longueur maximale en octets pour les données binaires, sous forme de caractères, de texte ou d'image.  Sinon, la valeur NULL est retournée.|  
|numeric\_precision|Octet non signé|Précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|numeric\_precision\_radix|Int16|Radical de précision des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|numeric\_scale|Int32|Échelle des données numériques approximatives, des données numériques exactes, des données entières ou des données monétaires.  Sinon, la valeur NULL est retournée.|  
|datetime\_precision|Int16|Code Subtype pour les types de données d'intervalle datetime et SQL\-92.  Pour les autres types de données, la valeur NULL est retournée.|  
|character\_set\_catalog|Chaîne|Retourne une liste maître indiquant la base de données dans laquelle l'ensemble de caractères se trouve et si la colonne contient des données de type caractères ou texte.  Sinon, la valeur NULL est retournée.|  
|character\_set\_schema|Chaîne|Retourne toujours NULL.|  
|character\_set\_name|Chaîne|Retourne le nom unique de l'ensemble de caractères si cette colonne contient des données de type caractère ou texte.  Sinon, la valeur NULL est retournée.|  
|collation\_catalog|Chaîne|Retourne une liste maître indiquant la base de données dans laquelle le classement est défini, si la colonne contient des données de type caractères ou texte.  Sinon, cette colonne a une valeur NULL.|  
|IS\_FILESTREAM|Chaîne|YES si la colonne présente l'attribut FILESTREAM.<br /><br /> NO si la colonne ne présente pas l'attribut FILESTREAM.|  
|IS\_SPARSE|Chaîne|YES s'il s'agit d'une colonne fragmentée.<br /><br /> NO s'il ne s'agit pas d'une colonne fragmentée.|  
|IS\_COLUMN\_SET|Chaîne|YES s'il s'agit d'une colonne d'ensemble de colonnes.<br /><br /> NO s'il ne s'agit pas d'une colonne d'ensemble de colonnes.|  
  
## Utilisateurs  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|uid|Int16|ID d'utilisateur, unique dans cette base de données.  1 est le propriétaire de base de données.|  
|name|Chaîne|Nom d'utilisateur ou nom de groupe, unique dans cette base de données.|  
|createdate|DateTime|Date d'ajout du compte.|  
|updatedate|DateTime|Date à laquelle le compte a été modifié pour la dernière fois.|  
  
## Vues  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|table\_catalog|Chaîne|Catalogue de la vue.|  
|table\_schema|Chaîne|Schéma contenant la vue.|  
|table\_name|Chaîne|Nom de la vue.|  
|check\_option|Chaîne|Type de WITH CHECK OPTION.  Est CASCADE si la vue originale a été créée à l'aide de WITH CHECK OPTION.  Dans le cas contraire, retourne NONE.|  
|is\_updatable|Chaîne|Indique si la vue peut être mise à jour.  Retourne toujours NO.|  
  
## ViewColumns  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|view\_catalog|Chaîne|Catalogue de la vue.|  
|view\_schema|Chaîne|Schéma contenant la vue.|  
|view\_name|Chaîne|Nom de la vue.|  
|table\_catalog|Chaîne|Catalogue de la table associée à cette vue.|  
|table\_schema|Chaîne|Schéma contenant la table associée à cette vue.|  
|table\_name|Chaîne|Nom de la table associée à cette vue.  Table de base.|  
|column\_name|Chaîne|Nom de la colonne.|  
  
## UserDefinedTypes  
  
|Nom de colonne|Type de données|Description|  
|--------------------|---------------------|-----------------|  
|assembly\_name|Chaîne|Nom du fichier pour l'assembly.|  
|UDT\_name|Chaîne|Nom de la classe pour l'assembly.|  
|version\_major|Objet|Numéro de version principale.|  
|version\_minor|Objet|Numéro de version secondaire.|  
|version\_build|Objet|Numéro de build.|  
|version\_revision|Objet|Numéro de révision.|  
|Culture\_info|Objet|Informations de culture associées à cet UDT.|  
|Public\_key|Objet|Clé publique utilisée par cet assembly.|  
|Is\_fixed\_length|Boolean|Indique si la longueur du type est toujours identique à max\_length.|  
|max\_length|Int16|Longueur maximale du type en octets.|  
|permission\_set\_desc|Chaîne|Nom convivial de l'ensemble d'autorisations\/niveau de sécurité pour l'assembly.|  
|create\_date|DateTime|Date à laquelle l'assembly a été créé\/enregistré.|  
  
## Voir aussi  
 [Récupération d'informations de schéma de base de données](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)