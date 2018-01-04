---
title: "Guide pratique pour définir le niveau de compression JPEG"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02e417fbcdb68e114ea0fc7afad7c22f6b2fdae9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="ae53c-102">Guide pratique pour définir le niveau de compression JPEG</span><span class="sxs-lookup"><span data-stu-id="ae53c-102">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="ae53c-103">Vous pouvez modifier les paramètres d’une image quand vous enregistrez l’image sur disque de façon à réduire la taille du fichier ou améliorer sa qualité.</span><span class="sxs-lookup"><span data-stu-id="ae53c-103">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="ae53c-104">Vous pouvez ajuster la qualité d’une image JPEG en changeant son niveau de compression.</span><span class="sxs-lookup"><span data-stu-id="ae53c-104">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="ae53c-105">Pour spécifier le niveau de compression lorsque vous enregistrez une image JPEG, vous devez créer un <xref:System.Drawing.Imaging.EncoderParameters> de l’objet et le passer à la <xref:System.Drawing.Image.Save%2A> méthode de la <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="ae53c-105">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="ae53c-106">Initialiser le <xref:System.Drawing.Imaging.EncoderParameters> objet afin qu’il possède un tableau qui se compose d’une <xref:System.Drawing.Imaging.EncoderParameter>.</span><span class="sxs-lookup"><span data-stu-id="ae53c-106">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="ae53c-107">Lorsque vous créez le <xref:System.Drawing.Imaging.EncoderParameter>, spécifiez la <xref:System.Drawing.Imaging.Encoder.Quality> encodeur et le niveau de compression souhaité.</span><span class="sxs-lookup"><span data-stu-id="ae53c-107">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae53c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="ae53c-108">Example</span></span>  
 <span data-ttu-id="ae53c-109">L’exemple de code suivant crée un <xref:System.Drawing.Imaging.EncoderParameter> de l’objet et enregistre trois images JPEG.</span><span class="sxs-lookup"><span data-stu-id="ae53c-109">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="ae53c-110">Chaque image JPEG est enregistrée avec un niveau de qualité différent, en modifiant le `long` valeur passée à la <xref:System.Drawing.Imaging.EncoderParameter> constructeur.</span><span class="sxs-lookup"><span data-stu-id="ae53c-110">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="ae53c-111">Un niveau de qualité de 0 correspond à la plus grande compression, et un niveau de qualité de 100 correspond à la compression minimale.</span><span class="sxs-lookup"><span data-stu-id="ae53c-111">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae53c-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ae53c-112">Compiling the Code</span></span>  
 <span data-ttu-id="ae53c-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="ae53c-113">This example requires:</span></span>  
  
-   <span data-ttu-id="ae53c-114">une application Windows Forms ;</span><span class="sxs-lookup"><span data-stu-id="ae53c-114">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="ae53c-115">A <xref:System.Windows.Forms.PaintEventArgs>, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ae53c-115">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
-   <span data-ttu-id="ae53c-116">Un fichier image nommé `TestPhoto.jpg` et qui se trouve sur **c:\\**.</span><span class="sxs-lookup"><span data-stu-id="ae53c-116">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae53c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae53c-117">See Also</span></span>  
 [<span data-ttu-id="ae53c-118">Guide pratique pour déterminer les paramètres pris en charge par un encodeur</span><span class="sxs-lookup"><span data-stu-id="ae53c-118">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 [<span data-ttu-id="ae53c-119">Types de bitmaps</span><span class="sxs-lookup"><span data-stu-id="ae53c-119">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [<span data-ttu-id="ae53c-120">Utilisation d’encodeurs et de décodeurs d’images dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="ae53c-120">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
