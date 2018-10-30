# form_validation_using-jquery
form validation and file upload using jquery
<!DOCTYPE html>
<html>
<head>
	<title>Form_validation with jquery</title>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css">
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
</head>
<body>

	<script>
		$(document).ready(function() {
			$('#submit').click(function(e) {

				var firstname = $('#fname').val();
				var lastname = $('#lname').val();
				var address = $('#add').val();
				var course = $("input[name=Course]:checked").val();
				var hobbies = $("input[name=hobbies]:checked").length;
				var subject = $("#subject").val();
				var fileupload = $("#fileupload")[0].files.length;
				var file = $('input[type="file"]').val();
	      		var exts = ['doc','docx','rtf','odt','html'];
	      		var file_size = $('#fileupload')[0].files[0].size;
	      	

				if(firstname == '')
   				 {
					  alert('Please enter your First Name');
		  			$('#fname').focus(); 
		  			 return false;
   				 }
   				 else if(lastname == '')
   				 {
					  alert('Please enter your Last Name');
		  			$('#lname').focus(); 
		  			 return false;
   				 }
   				else if(address == '')
   				 {
					  alert('Please enter your address');
		  			$('#add').focus(); 
		  			 return false;
   				 }
   				 else if (course === undefined)
   				 {
	           		 alert("Please enter your course.");
	           		  return false;

      			  }
      			  else if (hobbies < 1)
      			  {
	                alert("Please select at least 1 hobby");
	                 return false;
            	  }
	              else if (subject == "") 
	            	{
	               
		                alert("Please select a subject!");
		                return false;
	            	} 
            	 else if ($('#fileupload').get(0).files.length === 0) 
	            	{
	 				  alert("No files selected");
	 				  return false;
					}
				 else if ( file ) 
				 {
				   		 // split file name at dot
		       			 var get_ext = file.split('.');
		       			 // reverse name to check extension
		       			 get_ext = get_ext.reverse();
		       			 
		       			 // check file type is valid as given in 'exts' array
		       			 if ( $.inArray ( get_ext[0].toLowerCase(), exts ) > -1)
		       			 {
		       			   alert( 'Allowed extension!' );
		     			 }
		     			  else 
		     			  {
		       			  	 alert( 'Invalid file!' );
		     		  }
     			 }

	     		if(file_size>50)
	     		 {			
					alert("File is too big");
					return false;
				} 
            	else
            	{
            		return true;
            	}	      			
            
           });	 	
				
		});
	</script>
<form >

<div class = "row justify-content-center">
		<div class="col-6">
			<div class="jumbotron">
		
			<div class="form-group">
				<label> First name </label>
				<input type="text" id="fname"  /> </p>
				
			</div>
			<div class="form-group">
				<label> Last name </label>
				<input type="text" id="lname"  />
			</div>
			<div class="form-group">
				<label> Address </label>
				<textarea rows="4" cols="50" id="add"></textarea>
			</div>
			<div class="form-group">
				<label> Course : </label> 
				<input type="radio" name="Course"  value="BCA" > BCA <br>
				<input type="radio" name="Course" value="MCA" > MCA <br>
				<input type="radio" name="Course" value="BScIT"> BScIT <br>
				<input type="radio" name="Course" value="MScIT"> MScIT <br>
			</div>
			<div class="form-group">
				<label> Hobbies : </label> 
				<input type="checkbox" name="hobbies" value="Music"/> Music <br>
				<input type="checkbox" name="hobbies" value="Reading"/> Reading <br>
				<input type="checkbox" name="hobbies" value="Singing"/> Singing <br>
				<input type="checkbox" name="hobbies" value="Swimming"/> Swimming <br>
				<input type="checkbox" name="hobbies" value="Writing"/> Writing <br>
			</div>
			<div class="form-group">
				<label> Fav. Subject </label>
				<select name="subject" id="subject">
					<option value="">  Choose one </option>
					<option value="Java"> Java </option>
					<option value="PHP"> PHP </option>
					<option value="Javascript"> Javascript </option>
					<option value="IOS">  IOS</option>
					<option value="Android"> Android </option>
					<option value="Others"> Others </option>
				</select>
			</div class="form-group">

			<input type="submit" id="submit" value="submit" class='btn btn-success' /> 
			
			<input type="file" id="fileupload" >
		</div>
	</div>
</div>
</form>
</body>
</html>
