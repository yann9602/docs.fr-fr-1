---
title: "S&#233;curit&#233; et s&#233;rialisation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité du code, sérialisation"
  - "codage sécurisé, sérialisation"
  - "sécurité (.NET Framework), sérialisation"
  - "sérialisation, sécurité"
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# S&#233;curit&#233; et s&#233;rialisation
Étant donné que la sérialisation peut permettre à tout autre code d’afficher ou de modifier les données d’instance d’objet qui seraient autrement inaccessibles, une autorisation spéciale est nécessaire pour que le code effectue la sérialisation : <xref:System.Security.Permissions.SecurityPermission> avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionFlag> spécifié. Dans le cadre de la stratégie par défaut, cette autorisation n'est pas accordée à du code téléchargé depuis Internet ou un intranet ; seul le code sur l'ordinateur local reçoit cette autorisation.  
  
 Normalement, tous les champs d’une instance d’objet sont sérialisés, ce qui signifie que les données sont représentées dans les données sérialisées pour l’instance. Le code capable d’interpréter le format a la possibilité de déterminer la nature des valeurs de données, indépendamment de l’accessibilité du membre. De même, la désérialisation extrait des données de la représentation sérialisée et définit l’état de l’objet directement, encore une fois, quelles que soient les règles d’accessibilité.  
  
 Si possible, tout objet pouvant contenir des données de sécurité sensibles doit être non sérialisable. S’il doit être sérialisable, essayez de définir les champs spécifiques qui contiennent des données sensibles en tant que non sérialisables. Si cette opération ne peut pas être effectuée, n’oubliez pas que ces données sont exposées à tout code ayant l’autorisation de sérialiser, et assurez\-vous qu’aucun code malveillant ne peut obtenir cette autorisation.  
  
 L’interface <xref:System.Runtime.Serialization.ISerializable> est conçue pour être utilisée uniquement par l’infrastructure de sérialisation. Toutefois, si elle est non protégée, elle risque de révéler des informations sensibles. Si vous fournissez une sérialisation personnalisée en implémentant **ISerializable**, veillez à prendre les précautions suivantes :  
  
-   La méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> doit être sécurisée de manière explicite en demandant l’autorisation **SecurityPermission** avec **SerializationFormatter** spécifié, ou en faisant en sorte qu’aucune information sensible ne soit divulguée avec la sortie de la méthode. Exemple :  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _ Sub GetObjectData(info As SerializationInfo, context As StreamingContext) End Sub  
  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter =true)] public override void GetObjectData(SerializationInfo info, StreamingContext context) { }  
    ```  
  
-   Le constructeur spécial utilisé pour la sérialisation doit également effectuer une validation de saisie complète et doit être protégé ou privé pour assurer la protection contre une mauvaise utilisation par du code malveillant. Il doit appliquer les mêmes vérifications de sécurité et autorisations nécessaires pour obtenir une instance de cette classe par d’autres moyens, par exemple, en créant explicitement la classe ou en la créant indirectement par le biais d’un type de fabrique.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)