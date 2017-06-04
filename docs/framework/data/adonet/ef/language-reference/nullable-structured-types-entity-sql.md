---
title: "Types structur&#233;s autorisant la valeur null (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Types structur&#233;s autorisant la valeur null (Entity SQL)
Une instance `null` d'un type structuré est une instance qui n'existe pas.  Cela est différent d'une instance existante dans laquelle toutes les propriétés ont des valeurs `null`.  
  
 Cette rubrique décrit les types structurés Nullable, y compris quels types sont Nullable et quels modèles de code produisent des instances `null` de types Nullable structurés.  
  
## Différents types structurés Nullable  
 Il existe trois sortes de types de structure Nullable :  
  
-   Types de ligne  
  
-   Types complexes.  
  
-   types d'entités  
  
## Modèles de code qui produisent des instances Null de types structurés  
 Les scénarios suivants produisent des instances `null` :  
  
-   Mise en forme de données `null` comme type structuré :  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Upcast d'un type de base vers un type dérivé :  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Jointure externe sur condition fausse :  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     \-\- ou  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     \-\- ou  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   Suppression d'une référence `null` :  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   Obtention d'ANYELEMENT à partir d'une collection vide :  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Recherche d'instances `null` de types structurés :  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine(“[NULL]”);  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## Voir aussi  
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)