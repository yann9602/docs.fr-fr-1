---
title: "API qui s&#39;appuient sur la r&#233;flexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# API qui s&#39;appuient sur la r&#233;flexion
Dans certains cas, l'utilisation de la réflexion dans du code n'est pas évidente, et la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)] ne conserve donc pas les métadonnées nécessaires au moment de l'exécution.  Cette rubrique décrit certaines API courantes ou des modèles de programmation courants qui ne sont pas considérés comme faisant partie de l'API de réflexion, mais dont l'exécution s'appuie sur la réflexion.  Si vous les utilisez dans votre code source, vous pouvez ajouter des informations au fichier de directives runtime \(.rd.xml\) pour que les appels de ces API ne lèvent pas d'exceptions, telles que [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), au moment de l'exécution.  
  
## Méthode Type.MakeGenericType  
 Vous pouvez instancier dynamiquement un type générique `AppClass<T>` en appelant la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=fullName> à l'aide d'un code tel que celui\-ci :  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Pour que ce code s'exécute correctement, plusieurs éléments de métadonnées sont nécessaires.  Le premier est constitué des métadonnées `Browse` pour le type générique non instancié, `AppClass<T>` :  
  
```  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Il permet à l'appel de méthode <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=fullName> de réussir et de retourner un objet <xref:System.Type> valide.  
  
 Toutefois, même quand vous ajoutez des métadonnées pour le type générique non instancié, l'appel de la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=fullName> lève une exception [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) :  
  
```  
  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
  
```  
  
 Vous pouvez ajouter la directive runtime suivante au fichier de directives runtime pour ajouter des métadonnées `Activate` pour l'instanciation spécifique sur `AppClass<T>` de <xref:System.Int32?displayProperty=fullName> :  
  
```  
  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
  
```  
  
 Chaque instanciation différente sur `AppClass<T>` nécessite une directive particulière si elle est créée avec la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=fullName> et qu'elle n'est pas utilisée de manière statique.  
  
## Méthode MethodInfo.MakeGenericMethod  
 Dans le cas d'une classe `Class1` avec une méthode générique `GetMethod<T>(T t)`, `GetMethod` peut être appelée par réflexion à l'aide d'un code tel que celui\-ci :  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Pour s'exécuter correctement, ce code nécessite plusieurs éléments de métadonnées :  
  
-   Les métadonnées `Browse` pour le type dont vous souhaitez appeler la méthode.  
  
-   Les métadonnées `Browse` pour la méthode que vous souhaitez appeler.  S'il s'agit d'une méthode publique, l'ajout de métadonnées `Browse` publiques pour le type conteneur comprend également la méthode.  
  
-   Les métadonnées dynamiques pour la méthode que vous souhaitez appeler, afin que le délégué d'appel de réflexion ne soit pas supprimé par la chaîne d'outils [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Si des métadonnées dynamiques sont manquantes pour la méthode, l'exception suivante est levée quand la méthode <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=fullName> est appelée :  
  
    ```  
  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
  
    ```  
  
 Les directives runtime suivantes garantissent que toutes les métadonnées nécessaires sont disponibles :  
  
```  
  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
  
```  
  
 Une directive `MethodInstantiation` est obligatoire pour chaque instanciation différente de la méthode qui est appelée dynamiquement, et l'élément `Arguments` est mis à jour pour refléter chaque argument d'instanciation différent.  
  
## Méthodes Array.CreateInstance et Type.MakeTypeArray  
 L'exemple suivant appelle les méthodes <xref:System.Type.MakeArrayType%2A?displayProperty=fullName> et <xref:System.Array.CreateInstance%2A?displayProperty=fullName> sur un type, `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Si aucune métadonnée de tableau n'est présente, l'erreur suivante se produit :  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 Les métadonnées `Browse` pour le type de tableau sont nécessaires à son instanciation de manière dynamique.  La directive runtime suivante permet l'instanciation dynamique de `Class1[]`.  
  
```  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## Voir aussi  
 [Prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md)   
 [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)