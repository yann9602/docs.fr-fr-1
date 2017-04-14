---
title: "Comment&#160;: configurer IIS&#160;5.0 et IIS&#160;6.0 pour d&#233;ployer des applications WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ajuster le paramètre d'expiration du contenu"
  - "applications, déployer"
  - "configurer des serveurs Web pour déployer des applications WPF"
  - "paramètre d'expiration du contenu, ajuster"
  - "déployer des applications"
  - "extensions de fichier, inscrire"
  - "types MIME, inscrire"
  - "enregistrer des extensions de fichier"
  - "enregistrer des types MIME"
  - "serveurs Web, configurer pour déployer des applications WPF"
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: configurer IIS&#160;5.0 et IIS&#160;6.0 pour d&#233;ployer des applications WPF
Vous pouvez déployer une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] à partir de la plupart des serveurs Web, tant qu'ils sont configurés avec les types [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] appropriés.  Par défaut, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] est configuré avec ces types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)], mais [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] et [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] ne le sont pas.  
  
 Cette rubrique décrit comment configurer [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] et [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] pour déployer des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
> [!NOTE]
>  Vous pouvez vérifier la présence de la chaîne *UserAgent* dans le Registre afin de déterminer si [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] est installé sur le système.  Pour plus de détails et pour obtenir un script qui examine la chaîne *UserAgent* afin de déterminer si [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] est installé sur un système, consultez [Détecter si .NET Framework 3.0 est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).  
  
<a name="content_expiration"></a>   
## Ajuster le paramètre de l'expiration du contenu  
 Vous devez ajuster le paramètre de l'expiration du contenu à 1 minute.  La procédure ci\-après montre comment effectuer cette opération avec [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].  
  
1.  Cliquez sur le menu **Démarrer**, pointez sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet \(IIS\)**.  Vous pouvez également lancer cette application à partir de la ligne de commande en indiquant « %SystemRoot%\\system32\\inetsrv\\iis.msc ».  
  
2.  Développez l'arborescence [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] jusqu'à ce que vous trouviez le nœud **Site Web par défaut**.  
  
3.  Cliquez avec le bouton droit sur **Site Web par défaut** et sélectionnez **Propriétés** dans le menu contextuel.  
  
4.  Sélectionnez l'onglet **En\-têtes HTTP** et cliquez sur « Activer l'expiration de contenu ».  
  
5.  Paramétrez l'option pour que le contenu expire après 1 minute.  
  
<a name="register_mime_types"></a>   
## Enregistrer des types MIME et des extensions de fichier  
 Vous devez enregistrer plusieurs types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] et extensions de fichier afin que le navigateur du système client puisse charger le gestionnaire approprié.  Vous devez ajouter les types suivants :  
  
|Extension|Type MIME|  
|---------------|---------------|  
|.manifest|application\/manifeste|  
|.xaml|application\/xaml\+xml|  
|.application|application\/x\-ms\-application|  
|.xbap|application\/x\-ms\-xbap|  
|.deploy|application\/octet\-stream|  
|.xps|application\/vnd.ms\-xpsdocument|  
  
> [!NOTE]
>  Vous n'avez pas besoin d'enregistrer les types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] ou extensions de fichier sur les systèmes client.  Ils sont inscrits automatiquement lorsque vous installez [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)].  
  
 L'exemple [!INCLUDE[TLA#tla_visualbscrpt](../../../../includes/tlasharptla-visualbscrpt-md.md)] suivant ajoute automatiquement les types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] nécessaires à [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].  Pour utiliser ce script, copiez le code dans un fichier .vbs sur votre serveur.  Puis, exécutez le script en exécutant le fichier à partir de la ligne de commande ou en double\-cliquant sur le fichier dans [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  L'exécution de ce script à plusieurs reprises crée plusieurs entrées de mappage [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] dans la métabase [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)].  
  
 Après avoir exécuté ce script, vous ne pouvez pas consulter de types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] supplémentaires à partir de [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)] [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)].  Toutefois, ces types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] ont été ajoutés à la métabase [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)].  Le script suivant affichera tous les types [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] dans la métabase [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)].  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 Enregistrez le script en tant que fichier \(par exemple, `DiscoverIISMimeTypes.vbs`\) `.vbs` et exécutez\-le à partir de l'invite de commandes à l'aide de la commande suivante :  
  
 `cscript DiscoverIISMimeTypes.vbs`