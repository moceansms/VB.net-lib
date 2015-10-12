VB.NET sample code for integration with MoceanSMS API Server.

With MoceanSMS REST API you can send and receive SMS message, query account balance and pricing info.

Read more over at dev.moceansms.com/restapi

Setup
--------------

1) Import the namespace into your code.
	
	Imports System.Net
	Imports System.IO
	Imports System.Xml
	Imports System.Text
	Imports ConsoleApplication2.MoceanNamespace

	Namespace MoceanNamespace
		Public Class MoceanSMSClass
			...
			...
			...
		End Class
	End Namespace	

2) This class can be called as follows:

	Dim res As Hashtable
	Dim MoceanClass As MoceanSMSClass = New MoceanSMSClass()
	res = MoceanClass.SendSMS("mocean-api-key", "mocean-api-secret", "mocean-from", "mocean-to", "Hello! How are you?")

Examples
--------------

1) Send SMS

    Imports ConsoleApplication1.MoceanNamespace
	Module MoceanSMS
		Sub Main()
			Dim res As Hashtable
			Dim MoceanClass As MoceanSMSClass = New MoceanSMSClass()

			res = MoceanClass.SendSMS("mocean-api-key", "mocean-api-secret", "mocean-from", "mocean-to", "Hello! How are you?")

			'Display all returned results
			For Each i In res
				Console.WriteLine(i.key + "=" + i.value)
			Next
		End Sub
	End Module


2) Query account balance

    Imports ConsoleApplication1.MoceanNamespace
	Module MoceanSMS
		Sub Main()
			Dim res As Hashtable
			Dim MoceanClass As MoceanSMSClass = New MoceanSMSClass()

			res = MoceanClass.CheckMoceanBalance("mocean-api-key", "mocean-api-secret")
			Console.WriteLine("status = " + res("status"))
			Console.WriteLine("value = " + res("value"))
		End Sub
	End Module 



3) Query message status

    Imports ConsoleApplication1.MoceanNamespace
	Module MoceanSMS
		Sub Main()
			Dim res As Hashtable
			Dim MoceanClass As MoceanSMSClass = New MoceanSMSClass()

			res = MoceanClass.MoceanMessageStatus("mocean-api-key", "mocean-api-secret", "mocean-msgid")
			Console.WriteLine("status = " + res("status"))
			Console.WriteLine("value = " + res("value"))
		End Sub
	End Module 
	
4) Get account pricing

    Imports ConsoleApplication1.MoceanNamespace
	Module MoceanSMS
		Sub Main()
			Dim res As Hashtable
			Dim MoceanClass As MoceanSMSClass = New MoceanSMSClass()

			res = MoceanClass.MoceanAccountPricing("mocean-api-key", "mocean-api-secret")
			Console.WriteLine("country = " + res("country"))
			Console.WriteLine("operator = " + res("operator"))
			Console.WriteLine("mcc = " + res("mcc"))
			Console.WriteLine("mnc = " + res("mnc"))
			Console.WriteLine("price = " + res("price"))
		End Sub
	End Module 
