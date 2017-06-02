---
title: "Configuration requise pour le fournisseur de donn&#233;es&#160;.NET Framework pour Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Configuration requise pour le fournisseur de donn&#233;es&#160;.NET Framework pour Oracle
Le fournisseur de données .NET Framework pour Oracle requiert l'installation de Microsoft Data Access Components \(MDAC\) version 2.6 ou ultérieure.  MDAC 2.8 SP1 est recommandé.  
  
 Oracle 8i Client version 3 \(8.1.7\) ou ultérieure doit également être installé.  
  
 Les logiciels clients Oracle antérieurs à la version Oracle 9i ne peuvent pas accéder aux bases de données UTF16 parce que UTF16 est une nouvelle fonction d'Oracle 9i.  Pour utiliser cette fonction, vous devez mettre à niveau votre logiciel client vers Oracle 9i ou une version ultérieure.  
  
## Utilisation du fournisseur de données pour Oracle et données Unicode  
 Voici une liste de problèmes en relation avec Unicode dont vous devez tenir compte lorsque vous utilisez le fournisseur de données .NET Framework pour Oracle et les bibliothèques du client Oracle.  Pour plus d'informations, voir la documentation Oracle.  
  
### Définition de la valeur Unicode dans un attribut de chaîne de connexion  
 Lorsque vous travaillez avec Oracle, vous pouvez utiliser l'attribut de chaîne de connexion  
  
```  
Unicode=True   
```  
  
 pour initialiser les bibliothèques du client Oracle en mode UTF\-16.  Cela a pour effet que les bibliothèques du client Oracle acceptent UTF\-16 \(qui est très similaire à UCS\-2\) à la place des chaînes multioctet.  Cela permet au fournisseur de données pour Oracle de pouvoir toujours travailler avec une page de code Oracle quelconque sans que cela nécessite un travail de conversion supplémentaire.  Cette configuration ne fonctionne que si vous utilisez des clients Oracle 9i pour communiquer avec une base de données Oracle 9i à l'aide de l'ensemble de caractères de remplacement de AL16UTF16.  Quand un client Oracle 9i communique avec un serveur Oracle 9i, des ressources supplémentaires sont requises pour convertir les valeurs **CommandText** Unicode dans l'ensemble de caractères multioctet approprié qu'utilise le serveur Oracle 9i.  Cela peut être évité lorsque vous savez que vous disposez de la configuration sécurisée en ajoutant `Unicode=True` à votre chaîne de connexion.  
  
### Mélange de versions de client Oracle et de serveur Oracle  
 Les clients Oracle 8i ne peuvent pas accéder aux données **NCHAR**, **NVARCHAR2** ou **NCLOB** dans des bases de données Oracle 9i lorsque l'ensemble de caractères nationaux du serveur est spécifié comme AL16UTF16 \(paramétrage par défaut pour Oracle 9i\).  Comme la prise en charge de l'ensemble de caractères UTF\-16 n'a été introduite qu'avec Oracle 9i, les clients Oracle 8i ne peuvent pas le lire.  
  
### Utilisation de données UTF\-8  
 Pour définir l'ensemble de caractères de remplacement, définissez la clé de registre HKEY\_LOCAL\_MACHINE\\SOFTWARE\\ORACLE\\HOMEID\\NLS\_LANG sur UTF8.  Pour plus d'informations, voir les notes d'installation Oracle sur votre plateforme.  Le paramétrage par défaut est l'ensemble de caractères principal de la langue dans laquelle vous installez le logiciel client Oracle.  Si vous ne définissez pas la langue de façon à ce qu'elle corresponde à l'ensemble de caractères de la langue nationale de la base de données à laquelle vous vous connectez, cela a pour effet que les liaisons de paramètres et de colonnes envoient ou reçoivent des données dans l'ensemble de caractères de votre base de données principale et non dans l'ensemble de caractères national.  
  
### OracleLob ne peut mettre à jour que des caractères complets.  
 Pour des raisons pratiques, l'objet <xref:System.Data.OracleClient.OracleLob> hérite de la classe Stream .NET Framework et fournit des méthodes **ReadByte** et **WriteByte**.  Il implémente également des méthodes telles que **CopyTo** et **Erase**, qui opèrent sur des sections d'objets **LOB** Oracle.  Par contraste, le logiciel client Oracle fournit un certain nombre d'API pour opérer avec les **LOB** de caractères \(**CLOB** et **NCLOB**\).  Toutefois, ces API n'opèrent que sur des caractères complets.  En raison de cette différence, le fournisseur de données pour Oracle implémente la prise en charge de **Read** et **ReadByte** pour opérer avec des données UTF\-16 en manipulant les octets.  Toutefois, les autres méthodes de l'objet **OracleLob** n'autorisent que les opérations sur des caractères complets.  
  
## Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)