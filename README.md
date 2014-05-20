Special MVC Validation Attributes
=================================

Special MVC validation attributes for cases when you need conditional validation or/and date comparison. 

##Attributes included

[ConditionlRequired] - for conditional requred validation

[DateValidator] - for validating date format

[DateFieldsCompare] - for date comparison of two date properties

[DateTimeNowComparison] - for date comparison with current date or datetime


##Example of usage



        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Web;
        using System.Web.Mvc;
        using MUtility.Validation;
        
        namespace TestWebApp.Models
        {
            public class FormModel
            {
                [ConditionlRequired("Text2", ErrorMessage = "Text1 Error Message")]
                public string Text1 { get; set; }
        
                public string Text2 { get; set; } 
            }
        }


