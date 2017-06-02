---
title: "bindingFailure MDA | Microsoft Docs"
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
  - "binding failure"
  - "binding, failures"
  - "MDAs (managed debugging assistants), binding failures"
  - "assemblies [.NET Framework], binding failures"
  - "managed debugging assistants (MDAs), binding failures"
  - "BindingFailure MDA"
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# bindingFailure MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `bindingFailure` est activé lorsque le chargement d'un assembly échoue.  
  
## Symptômes  
 Le code a tenté de charger un assembly à l'aide d'une référence statique ou de l'une des méthodes du chargeur, telles que <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>.  L'assembly n'est pas chargé et une exception <xref:System.IO.FileNotFoundException> ou <xref:System.IO.FileLoadException> est levée.  
  
## Cause  
 Un échec de liaison se produit lorsque le runtime n'est pas en mesure de charger un assembly.  Un échec de liaison peut être le résultat de l'une des situations suivantes :  
  
-   Le Common Language Runtime \(CLR\) ne trouve pas l'assembly demandé.  Cela peut arriver pour de nombreuses raisons ; par exemple, si l'assembly n'est pas installé ou si l'application n'est pas correctement configurée pour trouver l'assembly.  
  
-   Un scénario problématique courant est la transmission d'un type à un autre domaine d'application qui requiert que le CLR charge l'assembly contenant ce type dans l'autre domaine d'application.  Il peut s'avérer impossible pour le runtime de charger l'assembly si l'autre domaine d'application est configuré différemment du domaine d'application d'origine.  Par exemple, les deux domaines d'application peuvent avoir des valeurs de propriété <xref:System.AppDomain.BaseDirectory%2A> différentes.  
  
-   L'assembly demandé est endommagé ou n'est pas un assembly.  
  
-   Le code qui tente de charger l'assembly ne dispose pas des autorisations de sécurité d'accès du code appropriées pour charger les assemblys.  
  
-   Les informations d'identification de l'utilisateur ne fournissent pas les autorisations requises pour lire le fichier.  
  
## Résolution  
 La première étape consiste à déterminer pourquoi le CLR n'a pas pu être lié à l'assembly demandé.  Le fait que le runtime n'ait pas pu trouver ou charger l'assembly demandé peut avoir plusieurs causes, telles que les scénarios répertoriés dans la section Cause.  Les actions suivantes sont recommandées pour éliminer la cause de l'échec de liaison :  
  
-   Déterminez la cause à l'aide des données fournies par le MDA `bindingFailure` :  
  
    -   Exécutez l'[Fuslogvw.exe \(Assembly Binding Log Viewer\)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) pour lire les journaux d'erreurs produits par le Binder d'assembly.  
  
    -   Déterminez si l'assembly est à l'emplacement demandé.  Dans le cas des méthodes <xref:System.Reflection.Assembly.LoadFrom%2A> et <xref:System.Reflection.Assembly.LoadFile%2A>, l'emplacement demandé peut facilement être déterminé.  Dans le cas de la méthode <xref:System.Reflection.Assembly.Load%2A> qui peut être liée à l'aide de l'identité de l'assembly, vous devez rechercher des assemblys qui correspondent à cette identité dans le chemin de détection de la propriété <xref:System.AppDomain.BaseDirectory%2A> du domaine d'application et le Global Assembly Cache.  
  
-   Résolvez la cause selon la détermination précédente.  Les options de résolution possibles sont les suivantes :  
  
    -   Installez l'assembly demandé dans le GAC \(Global Assembly Cache\) et appelez la  méthode <xref:System.Reflection.Assembly.Load%2A> pour charger l'assembly par identité.  
  
    -   Copiez l'assembly demandé dans le répertoire de l'application et appelez la méthode <xref:System.Reflection.Assembly.Load%2A> pour charger l'assembly par identité.  
  
    -   Reconfigurez le domaine d'application dans lequel l'échec de liaison s'est produit pour inclure le chemin d'assembly en modifiant la propriété <xref:System.AppDomain.BaseDirectory%2A> ou en ajoutant des chemins de détection privés.  
  
    -   Modifiez la liste de contrôle d'accès pour le fichier afin de permettre à l'utilisateur connecté de lire le fichier.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  Il signale uniquement des données relatives aux échecs de liaison.  
  
## Sortie  
 Le MDA signale l'assembly dont le chargement a échoué, y compris le chemin d'accès demandé et\/ou le nom complet, le contexte de liaison, le domaine d'application dans lequel le chargement a été demandé et la raison de l'échec.  
  
 Le nom complet ou le chemin d'accès demandé peut être vide si ces données ne sont pas accessibles au CLR.  Si l'appel qui a échoué était un appel à la méthode <xref:System.Reflection.Assembly.Load%2A>, il est probable que le runtime n'ait pas pu déterminer le nom complet de l'assembly.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant illustre une situation qui peut activer ce MDA :  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## Voir aussi  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)