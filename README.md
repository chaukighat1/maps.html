<!DOCTYPE html> 
<html>
  <head>
	<script type="text/javascript" src="/javascript/jquery.js"></script>  
	<script type="text/javascript" src="/javascript/jquery.fileupload.js"></script> 
<script type="text/javascript">                                    
    $(function() {                                                   
      $('#fileupload').fileupload({                                  
        url: 'https://<%= BUCKET %>.s3.amazonaws.com/',       
        type: 'POST',                                                
        autoUpload: true,                                            
        formData: {                                                  
          key: "<%= "#{SecureRandom.uuid}/${filename}" %>",                                        
          AWSAccessKeyId: "<%= ACCESS_KEY_ID %>",                   
          acl: "public-read",                                        
          policy: "<%= policy %>",                                  
          signature: "<%= signature %>",                            
          success_action_status: "201"     
        }                                                            
      });                                                            
    });                                                              
</script>                                                          
  </head>
  <body>                                                                   
	<form action="/upload" method="post" enctype="multipart/form-data">
	  <input type="file" id="fileupload" name="file">                  
	  <input type="submit" value="Save">                               
	</form>                                                            
  </body>
</html>
