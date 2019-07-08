---
layout: post
title:      "Nested Routes "
date:       2019-07-08 02:53:43 +0000
permalink:  nested_routes
---


The purpose of router is to recognize URL and dispatch them to a controller's action. It also generates paths and URLs, avoiding the need to hardcode strings in your views.


1 resources :authors, only: %i[show index] do
2       resources :posts, only: %i[show index new edit]
3 end
4
5 resources :posts, only: %i[index show new create edit update]
-----------------------------------------------
*In the above method, that you will write in the routes.rb file, 'resources' in line 1 and 2 refers to the controller name, in this case 'authors'. The 'only:' calls upon specific files you want to access in your view folder. These view files are listed as '%i[show index new edit]'. The '%i' is a shortcut to writing out [:show, :index, :new, :edit].  
  
 Line 2 is indented because it is a nested route which is used when you want to assign parent/child relationships of models i.e:author/post, magazine/ad etc
		
Line 5 is the same code as line 2 and is repeated in order to show that you have a url associated directly with the :posts	controller.*
-----------------------------------------------		
6a  scope '/admin', module: 'admin' do  ---- if you want to use a different url name than the module is named
6b  namespace :admin do #-----if you want to use the same url and module name
7          resources :stats, only: [:index]
8     end
-----------------------------------------------
Line 6a 'scope' is defining the url name. The 'module' is assigning the asssociated controller folder. 
Line 6b is an alternate for line 6a. It can be used if you want to assign the same name to the url as the module name. 
*The caveat to line 6b is that the automaticly created helper method is prefixed with admin_, so stats_path becomes admin_stats_path. If you switch from 6a to 6b you have to remember to update any URL helpers you have in use in any of your mvc files. 

In line 7 'resources' is the controller assignment, in this case refering to the stats_controller. The views folder structure must match the controller folder structure.
-----------------------------------------------

