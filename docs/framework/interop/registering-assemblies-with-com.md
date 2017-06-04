---
title: "Registering Assemblies with COM | Microsoft Docs"
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
  - "COM interop, registering assemblies"
  - "unregistering assemblies"
  - "interoperation with unmanaged code, registering assemblies"
  - "registering assemblies"
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Registering Assemblies with COM
Vous pouvez exécuter un outil de ligne de commande appelé [outil Assembly Registration Tool \(Regasm.exe\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) pour inscrire ou annuler l'inscription d'un assembly à utiliser avec COM.  Regasm.exe ajoute des informations sur la classe à la base de registres pour que les clients COM peuvent utiliser la classe du .NET Framework de manière transparente.  La classe <xref:System.Runtime.InteropServices.RegistrationServices> fournit les fonctionnalités équivalentes.  
  
 Un composant managé doit être inscrit dans le Registre Windows avant de pouvoir être activé à partir d'un client COM.  Le tableau suivant contient les clés que Regasm.exe ajoute généralement au Registre Windows.  \(000000 indique la valeur GUID réelle.\)  
  
|GUID|Description|Clé de Registre|  
|----------|-----------------|---------------------|  
|CLSID|Identificateur de classe|HKEY\_CLASSES\_ROOT\\CLSID\\{000…000}|  
|IID|Identificateur d'interface|HKEY\_CLASSES\_ROOT\\Interface\\{000…000}|  
|LIBID|Identificateur de bibliothèque|HKEY\_CLASSES\_ROOT\\TypeLib\\{000…000}|  
|ProgID|Identificateur programmatique|HKEY\_CLASSES\_ROOT\\000…000|  
  
 Dans la clé HKCR\\CLSID\\{0000…0000}, la valeur par défaut est le ProgID de la classe et deux nouvelles valeurs nommées s'y ajoutent, Class et Assembly.  Le runtime lit la valeur d'assembly dans la base de registres et la passe au programme de résolution de l'assembly du runtime.  Le programme de résolution de l'assembly tente de localiser l'assembly, en fonction des informations sur l'assembly telles que le nom et le numéro de version.  Pour que le programme de résolution d'assembly trouve un assembly, l'assembly doit figurer dans l'un des emplacements suivants :  
  
-   Le Global Assembly Cache \(il doit s'agir d'un assembly avec nom fort\).  
  
-   Le répertoire de l'application.  Les assemblys chargés à partir du chemin d'accès de l'application ne sont accessibles qu'à partir de cette application.  
  
-   Avec un chemin de fichier spécifié avec l'option **\/codebase** à Regasm.exe.  
  
 Regasm.exe crée également la clé InProcServer32 dans la clé HKCR\\CLSID\\{0000…0000}.  Le nom de la DLL qui initialise le Common Language Runtime \(Mscoree.dll\) est affecté par défaut à la clé.  
  
## Examen des entrées du Registre  
 COM Interop assure l'implémentation d'une fabrique de classe standard pour créer une instance de toute classe .NET Framework.  Les clients peuvent appeler **DllGetClassObject** sur la DLL managée pour obtenir une fabrique de classe et créer des objets, comme ils le feraient avec tout autre composant COM.  
  
 Pour la sous\-clé d' `InprocServer32`, une référence à Mscoree.dll s'affiche à la place d'une bibliothèque de types COM traditionnelle indiquer que le common langage runtime crée l'objet managé.  
  
## Voir aussi  
 [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [How to: Reference .NET Types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)   
 [Calling a .NET Object](http://msdn.microsoft.com/fr-fr/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [Deploying an Application for COM Access](http://msdn.microsoft.com/fr-fr/fb63564c-c1b9-4655-a094-a235625882ce)