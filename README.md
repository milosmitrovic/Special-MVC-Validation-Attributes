Special MVC Validation Attributes
=================================

Special MVC validation attributes for cases when you need conditional validation or/and date comparison. 

##Attributes included

[ConditionlRequired] - for conditional requred validation

[DateValidator] - for validating date format

[DateFieldsCompare] - for date comparison of two date properties

[DateTimeNowComparison] - for date comparison with current date or datetime


##Example of usage


###Conditional Required Attribute

        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Web;
        using System.Web.Mvc;
        using mUtility.Validation;
        
        namespace TestWebApp.Models
        {
            public class FormModel
            {
                //Conditional required if "Text2" property is not null, empty or white space
                [ConditionlRequired("Text2", ErrorMessage = "Text1 Error Message")]
                public string Text1 { get; set; }
        
                public string Text2 { get; set; } 
                
            }
        }



###Date Validator Attribute

                //Optional date field validator
                [DateValidator(ErrorMessage = "Incorrect date format")]
                public string Birthday { get; set; }
        
                //Date validation with forced date format
                [DateValidator("dd-MM-yyyy", ErrorMessage = "Incorrect date format")]
                public string Birthday { get; set; }
        
                //Required date field with forced date format
                [DateValidator("dd-MM-yyyy", required: true, ErrorMessage = "Incorrect date format")]
                public string Birthday { get; set; }
                
                
                
###DateTimeNow Comparison Attribute

        //Compare date field with current datetime
        [DateTimeNowComparison(DateComparisonType.LowerThan, ErrorMessage = "Date of birth must be lower than current date")]
        public string Birthday { get; set; }
        
        //Compare date field only with current date
        [DateTimeNowComparison(DateComparisonType.Equal, onlyDate: true, ErrorMessage = "Date of birth must be equal to current date")]
        public string Birthday { get; set; }
        
        //Compare date field with current datetime and force date format
        [DateTimeNowComparison("dd-MM-yyyy", DateComparisonType.LowerThanOrEqual, ErrorMessage = "Date of birth must be lower than or equal to current date"))]
        public string Birthday { get; set; }
                
                
                
###Date Fields Compare Attribute

        //Comparison of two date fields
        [DateFieldsCompareValidator("DateTo",DateComparisonType.GreaterThan, ErrorMessage = "FromDate must be greater than ToDate")]
        public string FromDate { get; set; }
        
        [DateFieldsCompareValidator("FromDate",DateComparisonType.LowerThanOrEqual, ErrorMessage = "ToDate must be lower than or equal to FromDate")]
        public string ToDate { get; set; }
        
###Date Comparison Types

Available values of DateComparisonType enum:

        DateComparisonType.Equal;
        DateComparisonType.GreaterThan
        DateComparisonType.GreaterThanOrEqual
        DateComparisonType.LowerThan
        DateComparisonType.LowerThanOrEqual
