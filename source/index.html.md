---
title: EDluminate Institution API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='http://cyanna.com'>EDluminate powered by Cyanna</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the EDluminate Institution API. This API is provided to client institutions as a means to manage their EDlumiante data in whatever ways they need. These APIs are in Beta testing and are still in current development. Please feel more than free to contact Cyanna, EDluminate, and the technology team with any suggestions, problems, questions, etc.

Currently this API handles funneling leads into the EDluminate system. The next major API coming soon is the ability to export/pull data out of EDluminate for use in other systems, such as your Student Information System.

# Incoming Leads

> To funnel leads into the EDluminate application:

```shell
# With shell, you can just pass the correct parameters with each request
curl -d --data '{params}' "YOUR_INSTITUTION_SUBDOMAIN.edluminate.com/api/v1/contact_student_enrollment"
```

> The above command accepts JSON params structured like this:

```json
[
  {
    "email": "newlead@example.com",
    "first_name": "New",
    "last_name": "Lead",
    "phone_number": "9371234567",
    "prefered_contact_method": "email",
    "zipcode": "45440",
    "best_contact_time": "evening",
    "campus_id": "1",
    "source": "online",
    "notify": "false",
    "program_id": "2",
    "note": "Note via API",
    "api_access_key": "meowmeowmeow"
  }
]
```

> Make sure to replace `meowmeowmeow` with your API key.

EDluminate uses API keys to allow access to the API. You can request an API key by contacting Cyanna/EDluminate.

EDluminate expects for the API key to be included in all API requests to the server in the parameters named:

`'api_access_key': 'meowmeowmeow'`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

### HTTP Request

`POST http://YOUR_INSTITUTION_SUBDOMAIN.edluminate.com/api/v1/contact_student_enrollment`

<aside class="notice">
You must replace `YOUR_INSTITUTION_SUBDOMAIN` with your institutions EDlumiante subdomain.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
api_access_key | true | Institution API Access Key
email | true | New Lead's Email
first_name | true | New Lead's First Name
last_name | true | New Lead's Last Name
phone_number | true | New Lead's Phone Number (with area code)
campus_id | true | New Lead's Campus Preference. Must be ID of campus from EDluminate application.
program_id | true | New Leads's Program Preference. Must be ID of program from EDluminate application.
note | false | Note or comment to be associated with the new lead.
preferred_contact_method | false | New Lead's Preferred Means of Contact. Must be `email` or `mobile_phone`
zipcode | false | New Lead's Zip Code
best_contact_time | false | New Lead's Preferred time of day to Contact. Must be `morning`, `afternoon`, or `evening`
source | false | Source of New Lead Information. Options are: `online`, `facebook`, `google_adwords`, `linkedin`, `referral`, `personally_developed_lead`, `government`, `radio`, `print`, `event`, `phone`, `email`, `live_chat`, `tv`, `direct_mail`, `military`, `walk_in`, `ad_hoc`, `other`.
notify | false | Boolean that indicates if the student should be contacted by their preferred means. Must be `true` or `false`
