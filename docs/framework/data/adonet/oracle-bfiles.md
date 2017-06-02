---
title: "BFILE Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# BFILE Oracle
Le fournisseur de données .NET Framework pour Oracle inclut la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour opérer avec le type de données <xref:System.Data.OracleClient.OracleType> Oracle.  
  
 Le type de données **BFILE** Oracle est un type de données **LOB** Oracle contenant une référence à des données binaires ayant une taille maximale de 4 giga\-octets.  Un type de données **BFILE** Oracle diffère d'autres types de données **LOB** Oracle par ses données stockées dans un fichier physique du système d'exploitation et non sur le serveur.  Notez que le type de données **BFILE** fournit un accès en lecture seule aux données.  
  
 Autres caractéristiques du type de données **BFILE** qui le distinguent du type de données **LOB** :  
  
-   Il contient des données non structurées.  
  
-   Il prend en charge la fragmentation côté serveur.  
  
-   Il utilise une sémantique de copie de référence.  Par exemple, si vous effectuez une opération de copie sur un type de données **BFILE**, seule l'adresse **BFILE** \(qui est une référence au fichier\) est copiée.  Les données du fichier ne sont pas copiées.  
  
 Le type de données **BFILE** doit être utilisé pour référencer les LOB de grande taille, qu'il n'est en conséquence pas pratique de stocker dans la base de données.  Par rapport au type de données **LOB**, l'utilisation du type de données **BFILE** exige un temps système supplémentaire au niveau de la communication, du serveur et du client.  Il est plus efficace d'accéder à un type **BFILE** si vous avez uniquement besoin d'obtenir un petit volume de données.  Il est plus efficace d'accéder à des LOB résidant en mémoire si vous avez besoin d'obtenir l'objet entier.  
  
 Chaque objet **OracleBFile** différent de NULL est associé à deux entités qui définissent l'emplacement du fichier physique sous\-jacent :  
  
1.  Un objet DIRECTORY Oracle, qui est un alias de base de données pour un répertoire du système de fichiers.  
  
2.  Le nom du fichier physique sous\-jacent, qui se trouve dans le répertoire associé à l'objet DIRECTORY.  
  
## Exemple  
 L'exemple C\# suivant montre comment créer un type **BFILE** dans une table Oracle, puis l'extraire sous la forme d'un objet **OracleBFile**.  L'exemple montre l'utilisation de l'objet <xref:System.Data.OracleClient.OracleDataReader> et des méthodes **OracleBFile** **Seek** et **Read**.  Notez que, pour utiliser cet exemple, vous devez commencer par créer un répertoire nommé « c:\\\\bfiles » et un fichier nommé « MyFile.jpg » sur le serveur Oracle.  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)