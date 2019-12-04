## Async Task In Android

    //Passing the required data to perform operation in background
    new insertAsyncTask(recordsDao).execute(recordsDao);


    //AsyncTask class to contain async methods
    private static class insertAsyncTask extends AsyncTask<RecordsDao, Void, Void> { 
     
        private RecordsDao mAsyncTaskDao;
	    insertAsyncTask(RecordsDao dao) {  
	        mAsyncTaskDao = dao;  
	    }  
  
	    @Override   
	    protected Void doInBackground(RecordsDao... recordsDaos) { 

	        for (int i = 0; i < data.getValue().getData().size(); i++) {  
	            data.getValue().getData().get(i).setIs_synched(true);  
	            data.getValue().getData().get(i).setEvent_date(  
	                    Utility.dateString(SahayakApp.appContext, data.getValue().getData().get(i).getDatetime())  
	            );  
	        }  
	        mAsyncTaskDao.insertAll(data.getValue().getData());  
	        return null;  
	    }  
    }

