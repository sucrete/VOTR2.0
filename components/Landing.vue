<template>
  <div id="landing">
    <img src="static.png" class="static" />
    <div id="siteTitleWrapper">
      <h1 class="siteTitle" title="The">The</h1>
      <br />
      <h1 class="siteTitle" title="Voter's">Voter's</h1>
      <br />
      <h1 class="siteTitle" title="Companion">Companion</h1>
      <img class="fordFan" src="fordfan.png" />
    </div>
    <div id="informationWrapper">
      <div id="inputEverything">
        <!-- DO NOT CHANGE THE ID OF THIS INPUT! -->
        <input
          type="search"
          id="address-input"
          @input="updateValue($event.target.value)"
          placeholder="What is your address?"
        />
      </div>
      <div id="infoForTheUser">A voting utility designed to spark engagement, The Voter's Companion keeps you clued-in to elections happening in your region, on ways to vote, and who your representatives are. Enter your address. Get registered. Stay informed.</div>
      <img src="USA.svg" class="USA" />
      <img src="voteFoundationBadge.png" class="USVoteBadge" />
    </div>
  </div>
</template>

<script>

import places from "places.js";

export default {
  name: "Landing",
  data() {
    return {
      stateID: "",
// ██╗   ██╗ ██████╗ ████████╗███████╗██████╗      █████╗ ██████╗ ██╗
// ██║   ██║██╔═══██╗╚══██╔══╝██╔════╝██╔══██╗    ██╔══██╗██╔══██╗██║
// ██║   ██║██║   ██║   ██║   █████╗  ██████╔╝    ███████║██████╔╝██║
// ╚██╗ ██╔╝██║   ██║   ██║   ██╔══╝  ██╔══██╗    ██╔══██║██╔═══╝ ██║
//  ╚████╔╝ ╚██████╔╝   ██║   ███████╗██║  ██║    ██║  ██║██║     ██║
//   ╚═══╝   ╚═════╝    ╚═╝   ╚══════╝╚═╝  ╚═╝    ╚═╝  ╚═╝╚═╝     ╚═╝      
      voterAPI: {
        karuthers: "all that's fit to print",
        stateIDs: {
          meta: {
            offset: 0,
            limit: 56,
            total_objects: 56,
            next: null,
            previous: null,
          },
          objects: [
            {
              id: "S01",
              name: "Alabama",
              short_name: "AL",
              geo_id2: "01",
              fips: "01",
            },
            {
              id: "S02",
              name: "Alaska",
              short_name: "AK",
              geo_id2: "02",
              fips: "02",
            },
            {
              id: "S04",
              name: "Arizona",
              short_name: "AZ",
              geo_id2: "04",
              fips: "04",
            },
            {
              id: "S05",
              name: "Arkansas",
              short_name: "AR",
              geo_id2: "05",
              fips: "05",
            },
            {
              id: "S06",
              name: "California",
              short_name: "CA",
              geo_id2: "06",
              fips: "06",
            },
            {
              id: "S08",
              name: "Colorado",
              short_name: "CO",
              geo_id2: "08",
              fips: "08",
            },
            {
              id: "S09",
              name: "Connecticut",
              short_name: "CT",
              geo_id2: "09",
              fips: "09",
            },
            {
              id: "S10",
              name: "Delaware",
              short_name: "DE",
              geo_id2: "10",
              fips: "10",
            },
            {
              id: "S11",
              name: "District of Columbia",
              short_name: "DC",
              geo_id2: "11",
              fips: "11",
            },
            {
              id: "S12",
              name: "Florida",
              short_name: "FL",
              geo_id2: "12",
              fips: "12",
            },
            {
              id: "S13",
              name: "Georgia",
              short_name: "GA",
              geo_id2: "13",
              fips: "13",
            },
            {
              id: "S15",
              name: "Hawaii",
              short_name: "HI",
              geo_id2: "15",
              fips: "15",
            },
            {
              id: "S16",
              name: "Idaho",
              short_name: "ID",
              geo_id2: "16",
              fips: "16",
            },
            {
              id: "S17",
              name: "Illinois",
              short_name: "IL",
              geo_id2: "17",
              fips: "17",
            },
            {
              id: "S18",
              name: "Indiana",
              short_name: "IN",
              geo_id2: "18",
              fips: "18",
            },
            {
              id: "S19",
              name: "Iowa",
              short_name: "IA",
              geo_id2: "19",
              fips: "19",
            },
            {
              id: "S20",
              name: "Kansas",
              short_name: "KS",
              geo_id2: "20",
              fips: "20",
            },
            {
              id: "S21",
              name: "Kentucky",
              short_name: "KY",
              geo_id2: "21",
              fips: "21",
            },
            {
              id: "S22",
              name: "Louisiana",
              short_name: "LA",
              geo_id2: "22",
              fips: "22",
            },
            {
              id: "S23",
              name: "Maine",
              short_name: "ME",
              geo_id2: "23",
              fips: "23",
            },
            {
              id: "S24",
              name: "Maryland",
              short_name: "MD",
              geo_id2: "24",
              fips: "24",
            },
            {
              id: "S25",
              name: "Massachusetts",
              short_name: "MA",
              geo_id2: "25",
              fips: "25",
            },
            {
              id: "S26",
              name: "Michigan",
              short_name: "MI",
              geo_id2: "26",
              fips: "26",
            },
            {
              id: "S27",
              name: "Minnesota",
              short_name: "MN",
              geo_id2: "27",
              fips: "27",
            },
            {
              id: "S28",
              name: "Mississippi",
              short_name: "MS",
              geo_id2: "28",
              fips: "28",
            },
            {
              id: "S29",
              name: "Missouri",
              short_name: "MO",
              geo_id2: "29",
              fips: "29",
            },
            {
              id: "S30",
              name: "Montana",
              short_name: "MT",
              geo_id2: "30",
              fips: "30",
            },
            {
              id: "S31",
              name: "Nebraska",
              short_name: "NE",
              geo_id2: "31",
              fips: "31",
            },
            {
              id: "S32",
              name: "Nevada",
              short_name: "NV",
              geo_id2: "32",
              fips: "32",
            },
            {
              id: "S33",
              name: "New Hampshire",
              short_name: "NH",
              geo_id2: "33",
              fips: "33",
            },
            {
              id: "S34",
              name: "New Jersey",
              short_name: "NJ",
              geo_id2: "34",
              fips: "34",
            },
            {
              id: "S35",
              name: "New Mexico",
              short_name: "NM",
              geo_id2: "35",
              fips: "35",
            },
            {
              id: "S36",
              name: "New York",
              short_name: "NY",
              geo_id2: "36",
              fips: "36",
            },
            {
              id: "S37",
              name: "North Carolina",
              short_name: "NC",
              geo_id2: "37",
              fips: "37",
            },
            {
              id: "S38",
              name: "North Dakota",
              short_name: "ND",
              geo_id2: "38",
              fips: "38",
            },
            {
              id: "S39",
              name: "Ohio",
              short_name: "OH",
              geo_id2: "39",
              fips: "39",
            },
            {
              id: "S40",
              name: "Oklahoma",
              short_name: "OK",
              geo_id2: "40",
              fips: "40",
            },
            {
              id: "S41",
              name: "Oregon",
              short_name: "OR",
              geo_id2: "41",
              fips: "41",
            },
            {
              id: "S42",
              name: "Pennsylvania",
              short_name: "PA",
              geo_id2: "42",
              fips: "42",
            },
            {
              id: "S44",
              name: "Rhode Island",
              short_name: "RI",
              geo_id2: "44",
              fips: "44",
            },
            {
              id: "S45",
              name: "South Carolina",
              short_name: "SC",
              geo_id2: "45",
              fips: "45",
            },
            {
              id: "S46",
              name: "South Dakota",
              short_name: "SD",
              geo_id2: "46",
              fips: "46",
            },
            {
              id: "S47",
              name: "Tennessee",
              short_name: "TN",
              geo_id2: "47",
              fips: "47",
            },
            {
              id: "S48",
              name: "Texas",
              short_name: "TX",
              geo_id2: "48",
              fips: "48",
            },
            {
              id: "S49",
              name: "Utah",
              short_name: "UT",
              geo_id2: "49",
              fips: "49",
            },
            {
              id: "S50",
              name: "Vermont",
              short_name: "VT",
              geo_id2: "50",
              fips: "50",
            },
            {
              id: "S51",
              name: "Virginia",
              short_name: "VA",
              geo_id2: "51",
              fips: "51",
            },
            {
              id: "S53",
              name: "Washington",
              short_name: "WA",
              geo_id2: "53",
              fips: "53",
            },
            {
              id: "S54",
              name: "West Virginia",
              short_name: "WV",
              geo_id2: "54",
              fips: "54",
            },
            {
              id: "S55",
              name: "Wisconsin",
              short_name: "WI",
              geo_id2: "55",
              fips: "55",
            },
            {
              id: "S56",
              name: "Wyoming",
              short_name: "WY",
              geo_id2: "56",
              fips: "56",
            },
            {
              id: "S60",
              name: "American Samoa",
              short_name: "AS",
              geo_id2: "60",
              fips: "60",
            },
            {
              id: "S66",
              name: "Guam",
              short_name: "GU",
              geo_id2: "66",
              fips: "66",
            },
            {
              id: "S69",
              name: "Commonwealth of the Northern Mariana Islands",
              short_name: "MP",
              geo_id2: "69",
              fips: "69",
            },
            {
              id: "S72",
              name: "Puerto Rico",
              short_name: "PR",
              geo_id2: "72",
              fips: "72",
            },
            {
              id: "S78",
              name: "Virgin Islands",
              short_name: "VI",
              geo_id2: "78",
              fips: "78",
            },
          ],
        },
        electionInfo: {
          meta: {
            offset: 0,
            limit: 10,
            total_objects: 1,
            next: null,
            previous: null,
          },
          objects: [
            {
              id: 2882,
              created_at: "2020-01-11T16:22:03.005417Z",
              updated_at: "2020-08-24T23:44:56.005299Z",
              title: "Missouri General Election",
              state: {
                short_name: "MO",
                id: "S29",
                name: "Missouri",
              },
              election_level: {
                id: 18,
                name: "Federal",
              },
              election_type: {
                id: 2,
                name: "General",
              },
              election_type_detail: null,
              election_status: "approved",
              election_day_registration_is_available: false,
              use_overseas_dates_as_military_dates: true,
              election_date: "2020-11-03",
              is_public: true,
              additional_information: "",
              locations: [
                {
                  type: "state",
                  id: "S29",
                  geoid: "29",
                  name: "Missouri",
                },
              ],
              urls: [
                {
                  id: 1431,
                  url_type: {
                    id: 1,
                    name: "Election Web Site",
                  },
                  url: "http://www.sos.mo.gov/elections/govotemissouri",
                  name: "Missouri Voting",
                },
              ],
              dates: [
                {
                  id: 39442,
                  kind: "AVT",
                  date_type: {
                    id: 49,
                    default: false,
                    name: "In the Election Office by",
                  },
                  date: "2020-11-02",
                  time: "17:00:00",
                  time_zone: "US/Central",
                  time_zone_offset: "-0500",
                  date_human_readable:
                    "In the Election Office by Mon Nov 2, 2020 5:00PM CST",
                },
                {
                  id: 39443,
                  kind: "DBED",
                  date_type: {
                    id: 1,
                    default: true,
                    name: "Blank - (Date Only - No Descriptive Label)",
                  },
                  date: "2020-11-03",
                  time: "19:00:00",
                  time_zone: "US/Central",
                  time_zone_offset: "-0500",
                  date_human_readable: "Tue Nov 3, 2020 7:00PM CST",
                },
                {
                  id: 39444,
                  kind: "DBRD",
                  date_type: {
                    id: 10,
                    default: false,
                    name: "Received by",
                  },
                  date: "2020-10-21",
                  time: "17:00:00",
                  time_zone: "US/Central",
                  time_zone_offset: "-0500",
                  date_human_readable:
                    "Received by Wed Oct 21, 2020 5:00PM CDT",
                },
                {
                  id: 39445,
                  kind: "DRD",
                  date_type: {
                    id: 9,
                    default: false,
                    name: "Postmarked by",
                  },
                  date: "2020-10-07",
                  time: null,
                  time_zone: null,
                  time_zone_offset: null,
                  date_human_readable: "Postmarked by Wed Oct 7, 2020",
                },
                {
                  id: 39446,
                  kind: "MRD",
                  date_type: {
                    id: 52,
                    default: false,
                    name: "Away from US on Active Duty by",
                  },
                  date: "2020-11-03",
                  time: null,
                  time_zone: null,
                  time_zone_offset: null,
                  date_human_readable:
                    "Away from US on Active Duty by Tue Nov 3, 2020",
                },
                {
                  id: 39447,
                  kind: "OBED",
                  date_type: {
                    id: 9,
                    default: false,
                    name: "Postmarked by",
                  },
                  date: "2020-11-02",
                  time: null,
                  time_zone: null,
                  time_zone_offset: null,
                  date_human_readable: "Postmarked by Mon Nov 2, 2020",
                },
                {
                  id: 39448,
                  kind: "OBED",
                  date_type: {
                    id: 15,
                    default: false,
                    name: "Post received by",
                  },
                  date: "2020-11-06",
                  time: "12:00:00",
                  time_zone: "US/Central",
                  time_zone_offset: "-0500",
                  date_human_readable:
                    "Post received by Fri Nov 6, 2020 12:00PM CST",
                },
                {
                  id: 39449,
                  kind: "OBED",
                  date_type: {
                    id: 32,
                    default: false,
                    name: "Email or Fax by",
                  },
                  date: "2020-11-03",
                  time: "19:00:00",
                  time_zone: "US/Central",
                  time_zone_offset: "-0500",
                  date_human_readable:
                    "Email or Fax by Tue Nov 3, 2020 7:00PM CST",
                },
                {
                  id: 39450,
                  kind: "OBRD",
                  date_type: {
                    id: 10,
                    default: false,
                    name: "Received by",
                  },
                  date: "2020-10-21",
                  time: "17:00:00",
                  time_zone: "US/Central",
                  time_zone_offset: "-0500",
                  date_human_readable:
                    "Received by Wed Oct 21, 2020 5:00PM CDT",
                },
                {
                  id: 39451,
                  kind: "ORD",
                  date_type: {
                    id: 9,
                    default: false,
                    name: "Postmarked by",
                  },
                  date: "2020-10-07",
                  time: null,
                  time_zone: null,
                  time_zone_offset: null,
                  date_human_readable: "Postmarked by Wed Oct 7, 2020",
                },
              ],
              short_url: "https://api.usvotefoundation.org/e/cic/",
            },
          ],
        },
        
      },
      googleResponse: {
        data: {
          normalizedInput: {
            line1: "4153 Mercier Street",
            city: "Kansas City",
            state: "MO",
            zip: "64112"
          },
          kind: "civicinfo#representativeInfoResponse",
          divisions: {
            "ocd-division/country:us/state:mo": {
              name: "Missouri",
              officeIndices: [2, 4, 5, 6, 7, 8, 9, 10]
            },
            "ocd-division/country:us/state:mo/cd:5": {
              name: "Missouri's 5th congressional district",
              officeIndices: [3]
            },
            "ocd-division/country:us": {
              name: "United States",
              officeIndices: [0, 1]
            },
            "ocd-division/country:us/state:mo/county:jackson": {
              name: "Jackson County",
              officeIndices: [11, 12, 13, 14]
            }
          },
          offices: [
            {
              name: "President of the United States",
              divisionId: "ocd-division/country:us",
              levels: ["country"],
              roles: ["headOfState", "headOfGovernment"],
              officialIndices: [0]
            },
            {
              name: "Vice President of the United States",
              divisionId: "ocd-division/country:us",
              levels: ["country"],
              roles: ["deputyHeadOfGovernment"],
              officialIndices: [1]
            },
            {
              name: "U.S. Senator",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["country"],
              roles: ["legislatorUpperBody"],
              officialIndices: [2, 3]
            },
            {
              name: "U.S. Representative",
              divisionId: "ocd-division/country:us/state:mo/cd:5",
              levels: ["country"],
              roles: ["legislatorLowerBody"],
              officialIndices: [4]
            },
            {
              name: "Governor of Missouri",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              roles: ["headOfGovernment"],
              officialIndices: [5]
            },
            {
              name: "Lieutenant Governor of Missouri",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              roles: ["deputyHeadOfGovernment"],
              officialIndices: [6]
            },
            {
              name: "MO Secretary of State",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              officialIndices: [7]
            },
            {
              name: "MO State Treasurer",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              officialIndices: [8]
            },
            {
              name: "MO Attorney General",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              officialIndices: [9]
            },
            {
              name: "MO Supreme Court Judge",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              officialIndices: [10, 11, 12, 13, 14, 15, 16]
            },
            {
              name: "MO State Auditor",
              divisionId: "ocd-division/country:us/state:mo",
              levels: ["administrativeArea1"],
              officialIndices: [17]
            },
            {
              name: "Jackson County Sheriff",
              divisionId: "ocd-division/country:us/state:mo/county:jackson",
              levels: ["administrativeArea2"],
              officialIndices: [18]
            },
            {
              name: "Jackson County Prosecuting Attorney",
              divisionId: "ocd-division/country:us/state:mo/county:jackson",
              levels: ["administrativeArea2"],
              officialIndices: [19]
            },
            {
              name: "Jackson County Executive",
              divisionId: "ocd-division/country:us/state:mo/county:jackson",
              levels: ["administrativeArea2"],
              officialIndices: [20]
            },
            {
              name: "Jackson County Legislator",
              divisionId: "ocd-division/country:us/state:mo/county:jackson",
              levels: ["administrativeArea2"],
              officialIndices: [21, 22, 23]
            }
          ],
          officials: [
            {
              name: "Donald J. Trump",
              address: [
                {
                  line1: "1600 Pennsylvania Avenue Northwest",
                  city: "Washington",
                  state: "DC",
                  zip: "20500"
                }
              ],
              party: "Republican Party",
              phones: ["(202) 456-1111"],
              urls: ["https://www.whitehouse.gov/"],
              photoUrl:
                "https://www.whitehouse.gov/sites/whitehouse.gov/files/images/45/PE%20Color.jpg",
              channels: [
                {
                  type: "Facebook",
                  id: "DonaldTrump"
                },
                {
                  type: "Twitter",
                  id: "potus"
                },
                {
                  type: "YouTube",
                  id: "whitehouse"
                }
              ]
            },
            {
              name: "Mike Pence",
              address: [
                {
                  line1: "1600 Pennsylvania Avenue Northwest",
                  city: "Washington",
                  state: "DC",
                  zip: "20500"
                }
              ],
              party: "Republican Party",
              phones: ["(202) 456-1111"],
              urls: ["https://www.whitehouse.gov/"],
              photoUrl:
                "https://www.whitehouse.gov/sites/whitehouse.gov/files/images/45/VPE%20Color.jpg",
              channels: [
                {
                  type: "Facebook",
                  id: "mikepence"
                },
                {
                  type: "Twitter",
                  id: "VP"
                }
              ]
            },
            {
              name: "Roy Blunt",
              address: [
                {
                  line1: "260 Russell Senate Office Building",
                  city: "Washington",
                  state: "DC",
                  zip: "20510"
                }
              ],
              party: "Republican Party",
              phones: ["(202) 224-5721"],
              urls: ["https://www.blunt.senate.gov/"],
              photoUrl:
                "http://bioguide.congress.gov/bioguide/photo/B/B000575.jpg",
              channels: [
                {
                  type: "Facebook",
                  id: "SenatorBlunt"
                },
                {
                  type: "Twitter",
                  id: "RoyBlunt"
                },
                {
                  type: "YouTube",
                  id: "SenatorBlunt"
                },
                {
                  type: "YouTube",
                  id: "BluntforSenate2010"
                }
              ]
            },
            {
              name: "Josh Hawley",
              address: [
                {
                  line1: "212 Russell Senate Office Building",
                  city: "Washington",
                  state: "DC",
                  zip: "20510"
                }
              ],
              party: "Republican Party",
              phones: ["(202) 224-6154"],
              urls: ["https://www.hawley.senate.gov/"],
              emails: ["senator@hawley.senate.gov"],
              channels: [
                {
                  type: "Facebook",
                  id: "SenatorHawley"
                },
                {
                  type: "Twitter",
                  id: "SenHawleyPress"
                }
              ]
            },
            {
              name: "Emanuel Cleaver",
              address: [
                {
                  line1: "2335 Rayburn House Office Building",
                  city: "Washington",
                  state: "DC",
                  zip: "20515"
                }
              ],
              party: "Democratic Party",
              phones: ["(202) 225-4535"],
              urls: ["https://cleaver.house.gov/"],
              photoUrl:
                "http://bioguide.congress.gov/bioguide/photo/C/C001061.jpg",
              channels: [
                {
                  type: "Facebook",
                  id: "emanuelcleaverii"
                },
                {
                  type: "Twitter",
                  id: "repcleaver"
                },
                {
                  type: "YouTube",
                  id: "repcleaver"
                }
              ]
            },
            {
              name: "Michael L. Parson",
              address: [
                {
                  line1: "State Capitol Building",
                  line2: "201 West Capitol Avenue",
                  line3: "Room 224",
                  city: "Jefferson City",
                  state: "MO",
                  zip: "65101"
                }
              ],
              party: "Republican Party",
              phones: ["(573) 751-3222"],
              urls: ["https://governor.mo.gov/"],
              photoUrl:
                "https://ltgov.mo.gov/wp-content/uploads/2017/01/Parson-headshot.jpg",
              emails: ["ltgovinfo@ltgov.mo.gov"],
              channels: [
                {
                  type: "Facebook",
                  id: "GovMikeParson"
                },
                {
                  type: "Twitter",
                  id: "GovParsonMO"
                }
              ]
            },
            {
              name: "Mike Kehoe",
              address: [
                {
                  line1: "201 West Capitol Avenue",
                  city: "Jefferson City",
                  state: "MO",
                  zip: "65101"
                }
              ],
              party: "Republican Party",
              phones: ["(573) 751-4727"],
              urls: ["https://ltgov.mo.gov/"],
              channels: [
                {
                  type: "Facebook",
                  id: "MoLtGovMikeKehoe"
                },
                {
                  type: "Twitter",
                  id: "LtGovMikeKehoe"
                }
              ]
            },
            {
              name: "John R. Ashcroft",
              address: [
                {
                  line1: "201 West Capitol Avenue",
                  city: "Jefferson City",
                  state: "MO",
                  zip: "65101"
                }
              ],
              party: "Republican Party",
              phones: ["(573) 751-4936"],
              urls: ["https://www.sos.mo.gov/"],
              emails: ["info@sos.mo.gov"],
              channels: [
                {
                  type: "Facebook",
                  id: "MissouriSOS"
                },
                {
                  type: "Twitter",
                  id: "MissouriSOS"
                }
              ]
            },
            {
              name: "Scott Fitzpatrick",
              party: "Republican Party",
              phones: ["(573) 751-8533"],
              urls: ["https://www.treasurer.mo.gov/"],
              emails: ["info@treasurer.mo.gov"],
              channels: [
                {
                  type: "Facebook",
                  id: "MOTreasurer"
                },
                {
                  type: "Twitter",
                  id: "MOTreasurer"
                }
              ]
            },
            {
              name: "Eric Schmitt",
              party: "Republican Party",
              phones: ["(573) 751-3321"],
              urls: ["https://www.ago.mo.gov/"],
              channels: [
                {
                  type: "Facebook",
                  id: "AttorneyGeneralSchmitt"
                },
                {
                  type: "Twitter",
                  id: "AGEricSchmitt"
                }
              ]
            },
            {
              name: "George W. Draper, III",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "Patricia Breckenridge",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "Paul C. Wilson",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "Zel M. Fischer",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "Laura Denvir Stith",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "Mary R. Russell",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "W. Brent Powell",
              party: "Nonpartisan",
              phones: ["(573) 751-4144"],
              urls: ["https://www.courts.mo.gov/page.jsp?id=27"]
            },
            {
              name: "Nicole Galloway",
              party: "Democratic Party",
              phones: ["(800) 347-8597"],
              urls: ["https://auditor.mo.gov/"],
              emails: ["moaudit@auditor.mo.gov"],
              channels: [
                {
                  type: "Facebook",
                  id: "NicoleGallowayCPA"
                },
                {
                  type: "Twitter",
                  id: "AuditorGalloway"
                }
              ]
            },
            {
              name: "Darryl Forte",
              address: [
                {
                  line1: "4001 Northeast Lakewood Court",
                  city: "Lee's Summit",
                  state: "MO",
                  zip: "64064"
                }
              ],
              party: "Democratic",
              phones: ["(816) 541-1969"],
              urls: ["https://www.jacksoncountysheriff.org/"],
              emails: ["sheriff@jacksongov.org"]
            },
            {
              name: "Jean Peters Baker",
              address: [
                {
                  line1: "415 East 12th Street",
                  city: "Kansas City",
                  state: "MO",
                  zip: "64106"
                }
              ],
              party: "Democratic",
              phones: ["(816) 881-3555"],
              urls: ["https://www.jacksoncountyprosecutor.com/"]
            },
            {
              name: "Frank White, Jr.",
              address: [
                {
                  line1: "415",
                  line2: "200 East 12th Street",
                  city: "Kansas City",
                  state: "MO",
                  zip: "64106"
                }
              ],
              party: "Democratic",
              phones: ["(816) 881-3333"],
              urls: ["http://www.jacksongov.org/395/County-Executive"],
              emails: ["mhennosy@jacksongov.org"]
            },
            {
              name: "Crystal Williams",
              address: [
                {
                  line1: "415 East 12th Street",
                  city: "Kansas City",
                  state: "MO",
                  zip: "64106"
                }
              ],
              party: "Democratic",
              phones: ["(816) 881-3464"],
              urls: [
                "https://www.jacksongov.org/704/2nd-District-At-Large-Crystal-Williams"
              ],
              emails: ["crystalwilliams@jacksongov.org"]
            },
            {
              name: "Tony Miller",
              address: [
                {
                  line1: "201 West Lexington Avenue",
                  city: "Independence",
                  state: "MO",
                  zip: "64050"
                }
              ],
              party: "Unknown",
              phones: ["(816) 881-4423"],
              urls: [
                "https://www.jacksongov.org/705/3rd-District-At-Large-Tony-Miller"
              ],
              emails: ["tmiller@jacksongov.org"]
            },
            {
              name: "Jalen Anderson",
              address: [
                {
                  line1: "415",
                  line2: "201 East 12th Street",
                  city: "Kansas City",
                  state: "MO",
                  zip: "64106"
                }
              ],
              party: "Democratic",
              phones: ["(816) 881-4477"],
              urls: [
                "https://www.jacksongov.org/1077/1st-District-At-Large-Jalen-Anderson"
              ],
              emails: ["JAnderson@jacksongov.org"]
            }
          ]
        }
      },
      form: {
        country: {
          label: null,
          data: {},
        },
      },
    };
  },
  methods: {
    updateValue(val) {
    }
  },
  mounted() {
    const placesAutocomplete = places({
      container: document.getElementById("address-input"),
      type: "address",
      countries: ["us"],
      autoselect: true,
      value: (suggestion) => {
        return suggestion;
      },
    });

    placesAutocomplete.on("change", (e) => {
      this.$router.push({ path: "/main" });
    });

    placesAutocomplete.on("clear", function () {
      const blank = null;
      this.updateValue(blank);
      // this.updatePostcode(blank);
    });
  },
  beforeDestroy() {
    // this.placesAutocomplete.destroy();
    // return false;
  },
};
</script>
<!-- if you add "scoped" next to your <style> tag your modal will not be a circle -->
<style >
footer {
  display: none;
}
#USSign {
  width: 65px;
  height: auto;
  position: absolute;
  right: 7.1em;
  bottom: 1.2em;
}
#voteWithThis {
  width: 65px;
  height: auto;
  position: absolute;
  right: 7.1em;
  bottom: 1.5em;
}
#app {
  background-color: #96a6c9;
}
#infoForTheUser {
  padding: 15px 35px 0px;
  color: rgb(217, 122, 92);
  width: 70%;
  font-family: "Roboto", sans-serif;
  font-weight: 400;
  position: relative;
  text-align: left;
  font-size: 1.4em;
  line-height: 1.3;
  text-shadow: 0px 0px 3px #FBFBFB;
}
a#usvLink,
a#usvLink:visited {
  color: #9cacce !important;
}
#usvLink {
  text-decoration: none;
  transition: all 0.5s;
  -webkit-transition: all 0.5s;
}
#usvLink::before {
  content: " ";
  display: block;
  position: absolute;
  border-bottom: solid 2px #dadee6;
  bottom: 40px;
  width: 40%;
  /* left: 6.3%; */
  margin: 0 auto;
  -webkit-transition: all 0.5s;
  transition: all 0.5s;
  /* z-index:-1; */
}
a#usvLink:hover {
  color: #668ee4 !important;
}
#usvLink:hover::before {
  border-bottom: solid 2px #668ee4bb;
}
#usVotersIcon {
  height: 120px;
  position: absolute;
  top: 13em;
}

#siteTitleWrapper {
  padding-bottom: 0.8em;
  position: relative;
}
.siteTitle:first-of-type {
  margin-top: 0.15em;
}
.siteTitle {
  z-index: 2;
  font-family: "Oswald", serif;
  color: rgb(34, 33, 31);
  text-align: left;
  font-size: 6.2em;
  line-height: 85%;
  font-weight: 600;
  padding-left: .9em;
  /* padding-top: .3em; */
  position: relative;
  text-transform: uppercase;
  top: 0.75em;
  /* text-shadow: 2px 2px 0 #0C3447, 5px 5px 0 #AF0022, 10px 10px 0 #00131E; */
}
.siteTitle::before {
  content: attr(title);
  position: absolute;
  -webkit-text-stroke: 0.06em #e9e9e9;
  left: 0;
  top: 0;
  padding-left: .9em;
  z-index: -1;
}
.fordFan {
  position: absolute;
  width: 36%;
  right: 9%;
  top: 9%;
  z-index: 50;
}
#landing {
  position: relative;
  background-repeat: no-repeat;
  outline: 5px dotted #6d7dada8;
  outline-offset: -25px;
  height: 865px;
  background: url(../static/exclamation.svg);
  background-size: 100%;
  background-position: 20% -140%;
  background-repeat: no-repeat;
  
}
.USVoteBadge {
  position: absolute;
  right: 24px;
  bottom: 20px;
  width: 145px;
  height: auto;
  /* filter: drop-shadow(0 1px 1px rgba(0,0,0,0.04)) drop-shadow(0 2px 2px rgba(0,0,0,0.05))  drop-shadow(0 4px 4px rgba(0,0,0,0.06)) drop-shadow( 0 6px 6px rgba(0, 0, 0, .07));  */
}
.USA {
  position: absolute;
  top: 70px;
  right: 24px;
  width: 150px;
height: 100px;
}
#informationWrapper {
  background-color: #FBFBFB;
  width: 35em;
  height: 21.5em;
  border-radius: 0.5em;
  margin: 0 auto;
  position: relative;
  box-shadow: 0 1px 1px rgba(0,0,0,0.04), 
              0 2px 2px rgba(0,0,0,0.05), 
              0 4px 4px rgba(0,0,0,0.07);
  z-index: 200;
  background-color: #f5f3ee;
background-image: radial-gradient(
  circle farthest-corner at top left, rgb(242, 248, 232) 0%, rgba(240, 243, 217, 0) 50%),
    radial-gradient(
    circle farthest-side at top right, rgb(240, 223, 227) 0%, rgba(231, 219, 216, 0) 10%),
radial-gradient(circle farthest-corner at bottom right, rgba(228, 199, 188, 0.87) 0%, rgba(218, 157, 138, 0) 33%),
    radial-gradient(
    circle farthest-corner at top right, rgb(225, 224, 241) 0%, rgba(155, 221, 240,0) 50%),
  radial-gradient(ellipse at bottom center, rgb(241, 238, 222) 0%, rgba(254, 243, 159, 0) 80%);
}
.ap-dataset-places * {
  font-family: "Roboto", sans-serif;
}
#inputEverything {
  margin-top: 7em;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  margin-bottom: .7em;
  z-index: 90;

}
#address-input {
  padding-left: 15px;
  padding-top: 2px;
  display: block;
  color: #807b77;
  background-color: white;
  position: relative;
  /* width: 35em !important; */
  margin: 0 auto;
  outline: none;
  font-size: 1.15em;
  letter-spacing: 0.05em;
  font-family: "Roboto", sans-serif;
  font-weight: 500;
  transition: all 300ms ease-in-out;
  height: 38px;
  border-top-left-radius: 0.5em;
  border-top-right-radius: 0.5em;
  border-bottom-left-radius: 0em;
  border-bottom-right-radius: 0em;
  /* box-shadow: inset 0px 2px 6px 0px rgb(150, 153, 158), inset 0px 3px 12px -7px rgba(115, 117, 119, 0.65), 0 1px 1px 0px rgb(227, 229, 236); */
}

input:focus {
  outline: none;
  color: #605c59 !important;
  background-color: #dad7d5;
}
input:hover::-webkit-input-placeholder {
  color: #605c59 !important;
}
input:focus::-webkit-input-placeholder {
  color: #605c59 !important;
}
#address-input:hover {
  background-color: white !important;
}
#address-input:focus {
  color: #605c59 !important;
  background-color: white !important;
}
#address-input:focus {
  border-color: rgba(230, 134, 23, 0.9);
  /* box-shadow: 0 1px 1px rgba(229, 103, 23, 0.075) inset, 0 0 8px rgba(229, 103, 23, 0.6); */
  outline: 1 none;
}

/* #address-input:focus, #address-input:hover {
  box-shadow: inset 0 1px 1px 0px rgb(249, 249, 249);
} */
.ap-input {
  border: none !important;
}
.ap-input-icon.ap-icon-pin {
  right: 10px;

}
.ap-input-icon {
  transform: translateY(-18px);
}
.ap-input:hover ~ .ap-input-icon svg {
  fill: #6f6b68 !important;
}
.ap-input:focus ~ .ap-input-icon svg {
  fill: #6f6b68 !important;
}
.ap-input-icon svg {
  fill: #98938f !important;
  border: 0;
  background: transparent;
  position: relative;
  -webkit-transform: translateY(6%);
  transform: translateY(6%);
  outline: none;
  /* right: 5em; */
  /* top: .13em; */
}
.ap-icon-clear {
  right: 15px;
}
.theme--dark.v-application {
  color: unset;
}
.ap-dropdown-menu {
  margin-top: 0px;
  width: 35em;
  top: 2.4em !important;
  /* left: 5.45em !important; */
  border-top-left-radius: 0px !important;
  border-top-right-radius: 0px !important;
}
input:focus {
  outline: none;
  border: none;
  /* color: #6b6255 !important; */
  font-weight: 400;
  font-size: 100% !important;
}

input::placeholder {
  color: #807b77 !important;
}
.static {
  position: absolute;
  top: 0;
  left: 0;
  opacity: .5;
  height: 865px;
  width: 750px;
  z-index: 4;
  overflow: hidden;
}
@media screen and (max-width: 750px) {
  .siteTitle::before {
    content: unset;
  }
  #address-input {
    width: inherit;
    border-top-left-radius: 0.3em;
    border-top-right-radius: 0.3em;
  }
  #informationWrapper {
    width: 88vw;
    border-radius: 0.3em;
  }
  #landing {
    background-image: unset;
  }
  .ap-dropdown-menu {
    width: 88vw;
  }
  #topLine,
  #bottomLine {
    width: 90%;
  }
  .siteTitle:first-of-type {
    margin-top: unset;
  }
}
@media screen and (min-width: 250px) and (max-width: 320px) {
  #inputEverything {
    font-size: 100%;
  }
  #address-input {
    padding-left: 9px;
    position: absolute;
  }
  
  .logoBlock {
    width: 14.6rem;
    height: 11rem;
    left: 0px;
    top: 1rem;
  }
}
/* for iPhone 5 below for widths on iPhone 5-X (not "plus" sizes)*/
@media screen and (min-width: 365px) and (max-width: 413px) {
  #generous {
    display: none;
  }
  #informationWrapper {
    height: 27em;
  }
  .ap-dropdown-menu {
    width: 88vw !important;
  }
  .ap-input-icon.ap-icon-clear {
    right: -10px !important;
  }
  .ap-input-icon.ap-icon-pin {
    right: -13px;
  }
  #USVoteHeader,
  #infoForTheUser {
    font-size: 1.2em;
  }
  #USVoteHeader {
    padding: 0px 25px 0px;
  }
  #infoForTheUser {
    padding: 5px 25px 0px;
  }
  #landing {
    background-image: unset;
  }
  #voteWithThis {
    width: 95px;
    right: 3.4em;
    bottom: 17.5em;
  }
  #USSign {
    right: 3.5em;
    bottom: -16em;
    width: 50px;
  }
  .siteTitle {
    line-height: 70%;
  }
  #inputEverything {
    margin-bottom: 0.7em;
  }
  #usvLink::before {
    width: 59.7%;
    bottom: -2px;
  }
  #siteTitleWrapper {
    top: unset;
    padding-bottom: 0.2em;
  }
}
.v-application--wrap {
  min-height: unset;
}
@media screen and (max-width: 450px) {
  #infoAndStarsWrapper,
  .buttonWrapper,
  .spin3d > span {
    width: unset;
  }
}
/* below for screens widths on iPhone 5-8 */
@media screen and (max-width: 375px) {
  #app,
  body,
  #landing {
    width: 100vw;
    height: 100vw;
  }
  .ap-input-icon svg {
    right: 6vw;
  }
  .siteTitle {
    font-size: 3.5em;
    padding-left: 0.6em;
  }
}
@media screen and (min-width: 315px) and (max-width: 374px) {
  .logoBlock {
    top: 1.3rem;
    left: -1px;
  }
  .siteTitle {
    font-size: 2.9em !important;
  }

}

@media screen and (max-width: 375px) and (max-height: 700px) {
  #inputEverything {
    margin-top: 4.8em;
  }
}

@media screen and (min-width: 750px) {
  #usVotersIcon {
    right: 8em;
  }
}
@media screen and (min-width: 450px) and (max-width: 750px) {
  .siteTitle {
    padding-left: 12.5vw;
  }
  #usVotersIcon {
    right: 15vw;
  }
}
@media screen and (max-width: 692px) {
  * {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
}

/* below for iPhone 6/7/8 plus  */
@media screen and (min-width: 413px) and (max-width: 432px) {
  .siteTitle {
    padding-left: 8.5vw !important;
    font-size: 4.7em;
  }
  .ap-input-icon.ap-icon-pin {
    right: -20px;
  }
  .ap-input-icon.ap-icon-clear {
    right: -17px;
  }
  #generous {
    display: none;
  }
  #siteTitleWrapper {
    top: 20px;
  }
  .ap-dataset-places .ap-suggestions .ap-suggestion.ap-cursor {
    padding-left: 0.8vw;
  }
  .ap-input-icon svg {
    right: 7vw;
  }
  #usvLink::before {
    width: 57%;
  }
  #informationWrapper {
    height: 28em;
  }
  #voteWithThis {
    width: 95px;
    right: 3.4em;
    bottom: 36em;
  }
  #inputEverything {
    margin-bottom: 1em !important;
  }
  #USVoteHeader,
  #infoForTheUser {
    margin: 0 auto;
    font-size: 1.6em;
  }
  .ap-dropdown-menu {
    width: 88vw !important;
    left: 0em !important;
  }
}
@media screen and (min-width: 319px) and (max-width: 415px) {
}
@media screen and (min-width: 430) and (max-width: 750px) {
  .ap-input-icon {
    right: calc(2vw - 3vw * 0.9) !important;
    left: unset;
  }
}
@media screen and (min-width: 418px) and (max-width: 515px) {
  #infoAndStarsWrapper {
    padding-left: 6.3vw !important;
  }
  #USVoteHeader {
    padding-top: 4em;
    padding-left: 9vw;
    width: 92%;
  }
  .siteTitle {
    padding-left: 10vw !important;
  }
}
</style>
