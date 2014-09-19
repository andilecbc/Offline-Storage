	/* 
	*	This JavaScript API class allows you to interact with the local RHOM database and programmatically add models or get references to models.
	*	We have put the CRUD-(CREATE, READ, UPDATE, DELETE) methods sequentially for you.
	*	Make changes based on the commented sections below.
	*/
	
	
	//Model container declaration
	var modelContainer;                                  	
	
	//Creating a Model(Database)
	function createRhoModel(){	
		modelContainer = Rho.ORM.addModel(function(model) {
			model.modelName("Material"); 	                         //--Model Name
			model.property("Barcode", "string");			 //--Model Properties (Property name and return type)		
			model.property("Quantity", "integer"); 					  
			model.set("partition", "app");                           //--Partition types are("user", "local", or "app")
		});
	}; 

	//Adding records from a STRUCTURE, TABLE / COLLECTION (source).
	function addRecords(source){		
		if(source){
				var newRecord = modelContainer.create({          //--Add model record / object and save it to the database
					barcode	: source.BARCODE ,
					quantity: source.QUANTITY
				}); 
		}else{
			myMessageToast("Couldn't find or create records");				
		};	
		
		
	// Or use this implementation when parsing a table/collection
		
		/*
		if( source.length != 0 ){
			for (var i = 0; i < source.length; i++) { 
				var newRecord = modelContainer.create({
					barcode	: source[i].BARCODE ,
					quantity: source[i].QUANTITY
				});			 
			};				
		}else{
			myMessageToast("Couldn't find or create records ");				
		};
		*/
	};
	
	// Searching all records from the Model(Database)
	function searchRecords(objectId){
		var newRecord = materialModel.find( 'all' );
		var model = 'model'+ objectId;
		
		if(newRecord.length != 0){
			var syncData = new Array();
			for( var i = 0; i < newRecord.length ; i++ ){
				syncData.push({"BARCODE":newRecord[i].get('barcode'),"QUANTITY":newRecord[i].get('quantity')}); 
			};  
			window[model].setData(syncData);	
		}else{
			myMessageToast('No data on Local Database');
		};
	}; 	
		
	// Delete all products
	function deleteRecords( ){				

		var newRecord 	= modelContainer.find('all');               //--Read records from database	
		
		newRecord = modelContainer.deleteAll();                     //--Delete all records from database
		
		if( newRecord ){
			myMessageToast("Try delete again."); 			
		}else{
			myMessageToast("Deleted Product(s)");
		};
	};
