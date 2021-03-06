## Solution Guide: Part 2 - Defend Your SOC
   
### Windows Server Logs

#### Report Analysis for Severity

Did you detect any suspicious changes in severity?
	

- Yes. The percentages changed from:

	```
	High: 6.91%
	Informational: 93.09%
	```
	![Severity](/Images/Part_1-Activity/P1_Report_top_severity.PNG)
	to: 
	```
	High: 20.22%
	Informational: 79.78%
	```
	![Severity](/Images/Part_1-Activity/P1_Report_top_severity_windows_server_attack_logs.PNG)

- This indicates an increase in the high severity cases.

#### Report Analysis for Failed Activities

Did you detect any suspicious changes in failed activities?

- Yes. The percentages changed from:
	```
	success: 97.02%
	failure: 2.98%
	```
	![Status](/Images/Part_1-Activity/P1_Report_Windows_status.PNG)

	 to:
	```
	success: 98.44%
	failure: 1.56%
	```
	![Status](/Images/Part_1-Activity/P1_Report_top_status_windows_server_attack_logs.PNG)

- This indicates that there is not a major change in the cumulative failure of events. 
   
---
#### Alert Analysis for Failed Windows Activity

![Alert_Failed_Windows_Activity](/Images/Part_1-Activity/P1_Alert_for_Failed_Windows_Activity.PNG)

  - **_There is some potential suspicious activity for failed activity between 8 a.m. and 9 a.m. on Weds, March 25th._**

![Suspicious_Failed_Activity](/Images/Attack_Logs/P2-3_Suspicious_failed_Windows_activity.PNG)

  - **_The count of activity is 35 events during this hour, "A privileged service was called, where the user account was deleted, Domain Policies were changed, A user account was created, An attempt was made to reset an accounts password, and A computer account was deleted."_**
                
   
#### Alert Analysis for Successful Logons

![Alert_Anaylsis_for_Successful_Logons](/Images/Part_1-Activity/P1_Alert_Signatures_with_successfully_logged_on.PNG)

  - **_There is some potential suspicious activity for failed activity at 11 a.m and 12 p.m. on Weds, March 25th._**

![Account_was_Successfully_Logged_ON](/Images/Attack_Logs/P2-4_suspicious_volume_of_successful_logons.PNG)

  - **_The count of activity is 196 at 11 a.m. and 77 at 12 p.m._**

  - **_The primary user logging in is `user j`._**

![User_J](/Images/Attack_Logs/P2-4-a_suspicious_volume_of_successful_logons_user_j.PNG)

  - **_Yes, it would have alerted the SOC Analyst of the suspicious logons._**  
  - **_No, it is set appropriately for the hourly settings, it would have also triggered an alert for the activity for the second hour from 12 p.m. to 1 p.m. on the same day._**  

#### Alert Analysis for Deleted Accounts

Did you detect a suspicious volume of deleted accounts?  

![Alert_a_user_account_was_deleted](/Images/Part_1-Activity/P1_Alert_a_user_account_was_deleted.PNG)  

  - **_There was no suspicious activity of deleted accounts._**
![Suspicious_volume_of_deleted_accounts](/Images/Attack_Logs/P2-5_suspicious_volume_of_deleted_accounts.PNG)   
---
#### Dashboard Analysis for Time Chart of Signatures

- Does anything stand out as suspicious? What signatures stand out?
  - **_Yes, the signatures that have suspicious activity are: An attempt was made to reset a users password (39.955%), A user account was locked out (34.003%), and An account was successfully logged on (8.111%)._**

`Before Windows Server Attack Dashboard`

![Windows_Server_Monitoring_DashBoard](/Images/Part_1-Activity/P1_Windows_Server_Monitoring_DashBoard.PNG)
![Windows_Server_Monitoring_DashBoard-2](/Images/Part_1-Activity/P1_Windows_Server_Monitoring_DashBoard-2.PNG)

`Dashboad after the Windows Server Attack`
![Windows_Server_Monitoring_DashBoard_attacks_on_the_server](/Images/Part_2-Activity/P2_Windows_Server_Monitoring_DashBoard_attacks_on_the_server.PNG)
![Windows_Server_Monitoring_DashBoard_attacks_on_the_server-2](/Images/Part_2-Activity/P2_Windows_Server_Monitoring_DashBoard_attacks_on_the_server-2.PNG)

- What time did it start and stop for each signature? What is the peak count of the different signatures?

  - **_`A user account was locked out:` Started around `1 a.m. and ended at 3 a.m. on March 25th.` The peak count was `896`, and the total for the two hours was `(805 + 896 = 1701).`_**  
  - **_`An attempt was made to reset a users password:` Started around `9 a.m. and ended at 11 a.m. on March 25th.` The peak count was `1,258`, and the total for the two hours was `(1258 + 761 = 2019).`_**  
  - **_`The account was successfully logged on:` Started around `11 a.m. and ended at 1 p.m. on March 25th.` The peak count was `196`, and the total for the two hours was `(196 + 77 = 273).`_**  

![Dashboard_Signatures_attacks_logd](/Images/Attack_Logs/P2-1_Dashboard_Signatures_attacks_logd.PNG)

 #### Dashboard Analysis for Users

- Does anything stand out as suspicious? Which users stand out?

  - **_Yes, the users that have suspicious activity are users `A`, `K`, and `J`._**

- What time did it begin and stop for each user? What is the peak count of the different user?

  - **_`User A:` Started around `1 a.m. and ended at 3 a.m. on March 25th.` Peak count was `984`, and the total for the two hours was `(799 + 984 = 1783).`_**
  - **_`User K:` Started around `9 a.m. and ended at 11 AM on March 25th.` Peak count was `1,256`, and the total for the two hours was `(1256 + 761 = 2017).`_**  
  - **_`User J:` Started around `11 a.m. and ended at 1 p.m. on March 25th.` Peak count was `196`, and the total for the two hours was `(196 + 82 = 278).`_**  

![Dashboard_Users_attacks_logd](/Images/Attack_Logs/P2-1_Dashboard_Users_attacks_logd.PNG)
    
#### Dashboard Analysis for Signatures with Bar, Graph, Pie Charts
- Does anything stand out as suspicious?
  - **_`No`_**
- Do the results match your findings in your time chart for signatures?
  - **_All Charts are showing the same information as above for the Signatures._**
			
#### Dashboard Analysis for Users with Bar, Graph, Pie Charts
- Does anything stand out as suspicious?
  - **_`No`_**
- Do the results match your findings in your time chart for users?
  - **_All Charts are showing the same information as above for the Users._**

#### **Dashboard Analysis for Users with Statistical Chart**   

- What would be the advantage/disadvantage of using this report, compared to the other user panels you created?

  - **_There is only one advantage of the stats chart, as it will only give the total count of the users activity or the percentage of the activity. However, the disadvantage of the stats chart compared to a chart will show a cumulative perspective, while a time chart shows the suspicious activity over a more specific, and shorter time frame._**
     
---


### Apache WebServer Logs 
   
#### Report Analysis for Methods

- Did you detect any suspicious changes in HTTP methods? If so, which one?
  - **_Yes, there was a suspicious change in the HTTP `POST method`, which was raised from `1%` to `29%`or the `count` jumped from `106` to `1324`._**

![Report_Differnt_HTTP_Methods](/Images/Part_2-Activity/P2_Report_Differnt_HTTP_Methods.PNG)
![Report_Differnt_HTTP_Methods_attacks_logs](/Images/Part_2-Activity/P2_Report_Differnt_HTTP_Methods_attacks_logs.PNG)

- What is that method used for?

  - **_`POST` is used to submit or update information to a web server._**
							
   
#### Report Analysis for Referrer Domains

- Did you detect any suspicious changes in referrer domains?
	
  - **_There were no major suspicious referrers during the attack. Only minor changes to the first two domains by a couple of percentages._**

![Report_Top_10_Domains](/Images/Part_2-Activity/P2_Report_Top_10_Domains.PNG)
![Report_Top_10_Domains_attacks_logs](/Images/Part_2-Activity/P2_Report_Top_10_Domains_attacks_logs.PNG)

#### Report Analysis for HTTP Response Codes
- Did you detect any suspicious changes in HTTP response codes? 
									
  - **_There are several small changes, but the most prominent is the `404` response code, which increased from `2% to 15%`. The `200` response code went down from `91% to 83%`._**  

![Report_the_count_of_the_HTTP_response_codes](/Images/Part_2-Activity/P2_Report_the_count_of_the_HTTP_response_codes.PNG)  
![Report_the_count_of_the_HTTP_response_codes_attack_logs](/Images/Part_2-Activity/P2_Report_the_count_of_the_HTTP_response_codes_attack_logs.PNG)
    
---
#### Alert Analysis for International Activity

- Did you detect any suspicious volume of international activity? If so what was the count of the hour it occurred in?

  - **_There was activity in `Ukraine` between `8 p.m. and 9 p.m. on Weds, March 25th,` and had a count of `935` events._**
  - **_Yes, as the threshold was set at `200`, so this activity would be triggered as part of the alert._**  
  - **_No, as it???s above the activity set threshold._**  

![Alert_baseline_and_threshold_for_hourly_count_of_activity_from_a_country_other_than_the_United_States](/Images/Part_2-Activity/P2_Alert_baseline_and_threshold_for_hourly_count_of_activity_from_a_country_other_than_the_United_States.PNG)  
![Search_baseline_and_threshold_for_hourly_count_of_activity_from_a_country_other_than_the_United_States_attacks_logs](/Images/Part_2-Activity/P2_search_baseline_and_threshold_for_hourly_count_of_activity_from_a_country_other_than_the_United_States_attacks_logs.PNG)  


#### Alert Analysis for HTTP POST Activity

- Did you detect any suspicious volume of HTTP POST activity? If so, what was the count of the hour it occurred in and when did it occur?

  - **_There was a spike in `POST` method activity between `8 p.m. and 9 p.m. on Weds, March 25th`, and had a count of `1,296` events._**
  - **_No, the threshold set is at 15 counts, this would have been triggered._**

![Alert_baseline_and_threshold_for_hourly_count_of_the_HTTP_POST_method](/Images/Part_2-Activity/P2_Alert_baseline_and_threshold_for_hourly_count_of_the_HTTP_POST_method.PNG)  

---

#### Dashboard Analysis for Time Chart of HTTP Methods
  
- Does anything stand out as suspicious?
  - **_Yes, there were suspicious activities of the `POST` and `GET` method._**

- What was the method that seems to be used in the attack? What time did it begin and end, and what was the peak count?
  - **_The `POST` method was used, starting at `8 p.m. and ending at 9 p.m.` The peak count was `1,296`._**
  - **_The `GET` method was used, starting at `6 p.m. and ending at 7 p.m.` The peak count was `729`.

![Dashboard_Differnt_HTTP_Methods](/Images/Part_2-Activity/P2_Dashboard_Differnt_HTTP_Methods.PNG)  
    
 #### Dashboard Analysis for Cluster Map
  
- Does anything stand out as suspicious? What new country, city on the map has a high volume of activity?
  - **_Yes, there is suspicious activity in `Ukraine.`_**

![Apache WebServer Monitoring Dashboad_Top_10_countries](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad_Top_10_countries.PNG)  

- What is the count of that country, city?
  - **_When zoomed in, we can see the cities in `Ukraine` are:_**  
    - **_`Kiev:` Count of `439`_**  	
    - **_`Kharkiv:` Count of `433`_**  
    - **_`Lvov:` Count of `5`_**  

![Dashboard_location_based_on_the_clientip_field-Zoomed_on_Ukraine](/Images/Part_2-Activity/P2_Dashboard_location_based_on_the_clientip_field-Zoomed_on_Ukraine.PNG)

#### Dashboard Analysis for URI Data
- Does anything stand out as suspicious? What URI is being hit the most?
  - **_Yes, there is suspicious activity against the main VSI logon page: `/VSI_Account_logon.php`._**

![Dashboard_counts_of_different_URIs](/Images/Part_2-Activity/P2_Dashboard_counts_of_different_URIs.PNG)

- Based on the URI being accessed, what could the attacker potentially be doing?	
  - **_The attacker may be trying to brute force the VSI logon page._**


`Before Apache WebServer Logs Attack Dashboard`

![Apache_WebServer_Monitoring_Dashboad](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad.PNG)
![Apache_WebServer_Monitoring_Dashboad-1](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad-1.PNG)
![Apache_WebServer_Monitoring_Dashboad-2](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad-2.PNG)

`Dashboad after the Apache WebServer Logs Attack`  

![Apache WebServer Monitoring Dashboad_attack_logs](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad_attack_logs.PNG)
![Apache WebServer Monitoring Dashboad_attack_logs-1](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad_attack_logs-1.PNG)
![Apache WebServer Monitoring Dashboad_attack_logs-2](/Images/Part_2-Activity/P2_Apache_WebServer_Monitoring_Dashboad_attack_logs-2.PNG)

---
    

?? 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

---

## :sunglasses: `Ketan Vithal Patel` :sunglasses:  


### `Tuesday, August 3, 2021 -- UofT Cybersecurity - Boot Camp`
#### :rose::rose:`Jai Shri Swaminarayan`:rose::rose:
```
????????? ??????????????? ????????? ???????????????, ??????????????? ??????????????? ????????? ????????? |  Hare Krishna Hare Krishna, Krishna Krishna Hare Hare |
????????? ????????? ????????? ?????????, ????????? ????????? ????????? ????????? ||   Hare Ram Hare Ram, Ram Ram Hare Hare ||
```
---  
