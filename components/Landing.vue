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
      <img src="mauve2.png" class="USVoteBadge" />
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
        voterInfo: {
          meta: {
            offset: 0,
            limit: 10,
            total_objects: 1,
            next: null,
            previous: null,
          },
          objects: [
            {
              id: 139,
              state: {
                short_name: "MO",
                id: "S29",
                name: "Missouri",
              },
              eligibility_general_info: "",
              voting_general_info:
                "# Registration\r\n  \r\n## You can register to vote or update your registration information:\r\n  \r\n * online\r\n * by mail\r\n * in person at your elections office\r\n \r\n \r\n# Election Day Voting\r\n \r\n Polling places are open from 6am to 7pm on Election Day.\r\n \r\n## [Find my polling place](https://s1.sos.mo.gov/elections/voterlookup/)\r\n \r\n  \r\n# Early Voting\r\n \r\nYou can vote by absentee in the office of the local election authority until 5pm the night before the election. Contact your local election authority to inquire about hours and dates of operation.  \r\n\r\n \r\n# Absentee Voting\r\n\r\n## Registered voters can vote absentee if ONE of the following conditions applies: \r\n\r\n * You are absent on Election Day from the jurisdiction in which you are registered to vote \r\n * You are incapacitated or confined due to illness or physical disability, or a person who is primarily responsible for the physical care of a person who is incapacitated or confined due to illness or disability \r\n * You have religious beliefs or practices which prevent you from voting on Election Day \r\n * You are employed as an election authority, as a member of an election authority, or by an election authority at a location other than your polling place \r\n * You are incarcerated, provided all qualifications for voting are retained",
              voter_id_general_info: "",
              eligibility_requirements: [
                {
                  id: 342,
                  voter_type: {
                    id: 1,
                    kind: "D",
                    name: "Domestic Voter",
                  },
                  header: "You are eligible to vote in Missouri if you:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 62,
                        kind: "us_citizen",
                        name: "Are a U.S citizen",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 59,
                        kind: "state_resident",
                        name: "Are a resident of Missouri",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 68,
                        kind: "at_least_18_yo",
                        name: "Are at least 18 years old by Election Day",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 343,
                  voter_type: {
                    id: 1,
                    kind: "D",
                    name: "Domestic Voter",
                  },
                  header: "You are NOT eligible to vote in Missouri if:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 1,
                  items: [
                    {
                      item: {
                        id: 75,
                        kind: "in_prison",
                        name:
                          "You are in prison or detention or jail or penal institution",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 74,
                        kind: "on_parole_for_felony",
                        name:
                          "You are on parole for a felony conviction or convicted of a felony",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 71,
                        kind: "convicted_of_felony",
                        name:
                          "You were convicted of a felony or misdemeanor connected with voting",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 344,
                  voter_type: {
                    id: 1,
                    kind: "D",
                    name: "Domestic Voter",
                  },
                  header: "You may preregister to vote in Missouri",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 3,
                  items: [
                    {
                      item: {
                        id: 81,
                        kind: "pre_register_as_of_age_17_1/2",
                        name: "at the age of 17-1/2",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 417,
                  voter_type: {
                    id: 2,
                    kind: "O",
                    name: "Overseas Voter",
                  },
                  header:
                    "U.S. citizens living abroad have the right to vote as absentee voters, provided they are eligible to vote in their state. \r\n\r\nIf you are living outside of the U.S. permanently, indefinitely, or temporarily, your voting rights stay with you, even if you never voted when you lived in the U.S.\r\n\r\nTo vote from overseas:",
                  header_type: "M",
                  footer:
                    "Many states allow children who were born overseas, but never lived in the U.S., to use their U.S. parents’ last residence address to register.",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 86,
                        kind:
                          "complete_and_send_an_overseas_voter_registrationballot_request_form_to_your_election_office_in_the_us_this_is_one_specific_form_that_will_register_you_as_an_overseas_voter_and_request_your_absentee_ballot_simultaneously",
                        name:
                          "Complete and send an overseas voter registration/ballot request form to your election office in the U.S. This is one specific form that will register you as an overseas voter and request your absentee ballot – simultaneously.",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 477,
                  voter_type: {
                    id: 3,
                    kind: "M",
                    name: "Military Voter",
                  },
                  header:
                    "Service members and their eligible family members living outside their voting jurisdiction (within or outside the U.S.) are able to vote as absentee voters.",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 87,
                        kind:
                          "if_you_are_a_service_member_or_an_eligible_family_member_there_is_a_single_form_to_file_for_both_voter_registration_and_ballot_request_it_is_often_called_the_federal_post_card_application_or_the_fpca_form_this_form_must_be_re_filed_with_your_election_office_each_time_you_change_location",
                        name:
                          "If you are a service member, or an eligible family member, there is a single form to file for both voter registration and ballot request. It is often called the “Federal Post Card Application” or the FPCA form. This form must be re-filed with your election office each time you change location.",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 478,
                  voter_type: {
                    id: 3,
                    kind: "M",
                    name: "Military Voter",
                  },
                  header:
                    "To vote as a service member or eligible family member:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 1,
                  items: [
                    {
                      item: {
                        id: 85,
                        kind:
                          "complete_and_send_a_voter_registrationballot_request_form_fpca_to_your_election_office_in_the_us_it_is_the_same_form_in_all_states",
                        name:
                          "Complete and send a voter registration/ballot request form “FPCA” to your election office in the U.S. It is the same form in all states.",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 608,
                  voter_type: {
                    id: 4,
                    kind: "Student Voter",
                    name: "Student Eligibility",
                  },
                  header:
                    "If you are a student, you are eligible to vote in Missouri if:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 114,
                        kind: "college_another_state",
                        name: "You are attending college in another state",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 115,
                        kind: "out_of_state_student",
                        name:
                          "You reside in another state but attend college in Missouri",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 123,
                        kind: "new_student_id_from_state",
                        name:
                          "You provide a valid photo student ID from a college/university in Missouri at the polls",
                      },
                      position: 0,
                    },
                  ],
                },
              ],
              identification_requirements: [
                {
                  id: 105,
                  category: {
                    id: 1,
                    kind: "voter_registration",
                    name: "Voter Registration",
                    name_format: "",
                  },
                  header: "To register to vote in Missouri you should provide:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 79,
                        kind:
                          "the_last_four_digits_of_your_social_security_number",
                        name:
                          "The Last Four Digits of your Social Security Number",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 10,
                        kind: "your_state_name_drivers_license_number",
                        name: "Your Missouri Driver's License Number",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 106,
                  category: {
                    id: 1,
                    kind: "voter_registration",
                    name: "Voter Registration",
                    name_format: "",
                  },
                  header:
                    "If you are registering to vote for the first time by mail, you will need to provide a copy of a valid ID. Acceptable forms of ID include:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 1,
                  items: [
                    {
                      item: {
                        id: 72,
                        kind: "current_and_valid_photo_id",
                        name: "Current and Valid Photo ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 27,
                        kind: "valid_tribal_id",
                        name: "Valid Tribal ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 60,
                        kind:
                          "government_issued_document_that_shows_your_current_name_and_address",
                        name:
                          "Government Issued Document that shows your current name and address",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 43,
                        kind:
                          "utility_bill_bank_statement_government_check_or_paycheck_that_shows_your_current_name_and_address",
                        name:
                          "Utility Bill, Bank Statement, Government Check, or Paycheck that Shows your current name and address",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 56,
                        kind: "birth_certificate",
                        name: "Birth Certificate",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 65,
                        kind:
                          "other_proof_of_us_citizenship_issued_by_the_federal_government",
                        name:
                          "Other proof of US Citizenship issued by the Federal Government",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 134,
                  category: {
                    id: 2,
                    kind: "voting_in_person",
                    name: "Voting In-Person",
                    name_format: "",
                  },
                  header:
                    "In Missouri, you need to show a valid ID to vote. You can use any ID from this list:",
                  header_type: "M",
                  footer:
                    "If you do not have ID, you may still vote provisionally if you are registered and the signature matches.",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 171,
                        kind: "valid_military_id",
                        name: "Valid Military ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 98,
                        kind: "valid_state_non_drivers_id",
                        name: "Valid <State> non-driver's ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 177,
                        kind: "valid_state_name_drivers_license",
                        name: "Valid Missouri Driver's License",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 208,
                        kind: "valid_student_id_from_state_school",
                        name: "Valid Student ID from State School",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 24,
                        kind: "bank_statement_paycheck_or_government_check",
                        name: "Bank Statement, Paycheck or Government Check",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 115,
                        kind: "valid_us_passport",
                        name: "Valid US Passport",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 116,
                        kind: "valid_military_id",
                        name: "Valid Military ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 17,
                        kind: "utility_bill",
                        name: "Utility Bill",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 214,
                        kind: "voter_registration_card",
                        name: "Voter Registration Card",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 235,
                  category: {
                    id: 3,
                    kind: "voting_overseas",
                    name: "Voting Overseas",
                    name_format: "",
                  },
                  header:
                    "U.S. citizens living overseas may register and request a ballot using the overseas voter registration/ballot request form. You will have the following identification options when completing the form:",
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 245,
                        kind: "us_state_or_territory_or_district_issued_id",
                        name: "U.S. State or Territory or District Issued ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 246,
                        kind:
                          "option_to_indicate_that_you_do_not_have_the_requested_id",
                        name:
                          "Option to Indicate that you do not have the Requested ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 243,
                        kind: "last_4_digits_of_your_social_security_number",
                        name: "Last 4 Digits of your Social Security Number",
                      },
                      position: 0,
                    },
                  ],
                },
                {
                  id: 291,
                  category: {
                    id: 4,
                    kind: "voting_military",
                    name: "Voting Military",
                    name_format: "",
                  },
                  header:
                    'U.S. citizens living overseas may register and request a ballot using the overseas voter registration/ballot request form. You will have the following identification options when completing the form:\r\nService members and their dependents may register and request a ballot using the federal voter registration/ballot request form ("FPCA"). You will have the following identification options when completing the form:',
                  header_type: "M",
                  footer: "",
                  footer_type: "M",
                  position: 0,
                  items: [
                    {
                      item: {
                        id: 245,
                        kind: "us_state_or_territory_or_district_issued_id",
                        name: "U.S. State or Territory or District Issued ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 246,
                        kind:
                          "option_to_indicate_that_you_do_not_have_the_requested_id",
                        name:
                          "Option to Indicate that you do not have the Requested ID",
                      },
                      position: 0,
                    },
                    {
                      item: {
                        id: 243,
                        kind: "last_4_digits_of_your_social_security_number",
                        name: "Last 4 Digits of your Social Security Number",
                      },
                      position: 0,
                    },
                  ],
                },
              ],
              witness_notarization_requirements: [],
              transmission_methods: [
                {
                  id: 77,
                  voter_type: {
                    id: 2,
                    kind: "O",
                    name: "Overseas Voter",
                  },
                  additional_info:
                    "Voters who are in Federal service and are eligible to receive hostile fire, imminent danger pay, or are in a location designated as a combat zone may return their voted ballots by fax or email. \r\n\r\n(a) Members of the armed forces of the United States, while in active service, and their spouses and dependents; \r\n\r\n(b) Active members of the merchant marine of the United States and their spouses and dependents; \r\n\r\n(c) Civilian employees of the United States government working outside the boundaries of the United States, and their spouses and dependents; \r\n\r\n(d) Active members of religious or welfare organizations assisting servicemen, and their spouses and dependents; \r\n\r\n(e) Persons who have been honorably discharged from the armed forces or who have terminated their service or employment in any group mentioned in this section within sixty days of an election, and their spouses and dependents. \r\n\r\nPlease note that private email over the Internet is not a secure method of transfer for documents containing your confidential identity information. OVF strongly recommends regular mail and fax over email transfer.",
                  additional_info_type: "M",
                  items: [
                    {
                      id: 2252,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2253,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2254,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2255,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2256,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2257,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2258,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2259,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2260,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2261,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2262,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2263,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2264,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2265,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2266,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2277,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2278,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2279,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2280,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2281,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                  ],
                },
                {
                  id: 78,
                  voter_type: {
                    id: 1,
                    kind: "D",
                    name: "Domestic Voter",
                  },
                  additional_info: "",
                  additional_info_type: "M",
                  items: [
                    {
                      id: 2282,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2283,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2284,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2285,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2286,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2287,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2288,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2289,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2290,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2291,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2292,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2293,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2294,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2295,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2296,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2307,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2308,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2309,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2310,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2311,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                  ],
                },
                {
                  id: 79,
                  voter_type: {
                    id: 3,
                    kind: "M",
                    name: "Military Voter",
                  },
                  additional_info:
                    "Voters who are in Federal service and are eligible to receive hostile fire, imminent danger pay, or are in a location designated as a combat zone may return their voted ballots by fax or email. \r\n\r\n(a) Members of the armed forces of the United States, while in active service, and their spouses and dependents; \r\n\r\n(b) Active members of the merchant marine of the United States and their spouses and dependents; \r\n\r\n(c) Civilian employees of the United States government working outside the boundaries of the United States, and their spouses and dependents; \r\n\r\n(d) Active members of religious or welfare organizations assisting servicemen, and their spouses and dependents; \r\n\r\n(e) Persons who have been honorably discharged from the armed forces or who have terminated their service or employment in any group mentioned in this section within sixty days of an election, and their spouses and dependents. \r\n\r\nPlease note that private email over the Internet is not a secure method of transfer for documents containing your confidential identity information. OVF strongly recommends regular mail and fax over email transfer.",
                  additional_info_type: "M",
                  items: [
                    {
                      id: 2312,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2313,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2314,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2315,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2316,
                      document_type: {
                        id: 4,
                        kind: "blank_ballot_to_voter",
                        name: "Blank Ballot To Voter",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2317,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2318,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2319,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2320,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2321,
                      document_type: {
                        id: 2,
                        kind: "absentee_ballot_request",
                        name: "Absentee Ballot Request",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2322,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2323,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2324,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2325,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2326,
                      document_type: {
                        id: 3,
                        kind: "voted_absentee_ballot_return",
                        name: "Voted-Absentee Ballot Return",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2337,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 1,
                        kind: "in_person",
                        name: "In-Person",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2338,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 2,
                        kind: "mail",
                        name: "Mail",
                      },
                      allowed: true,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2339,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 4,
                        kind: "fax",
                        name: "Fax",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2340,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 3,
                        kind: "email",
                        name: "Email",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                    {
                      id: 2341,
                      document_type: {
                        id: 1,
                        kind: "voter_registration",
                        name: "Voter Registration",
                      },
                      document_transmission_method: {
                        id: 5,
                        kind: "online",
                        name: "Online",
                      },
                      allowed: false,
                      additional_info: "",
                      additional_info_type: "M",
                    },
                  ],
                },
              ],
              lookup_tools: [
                {
                  id: 152,
                  lookup_tool: {
                    id: 5,
                    kind: "election_information",
                    name: "State Elections Website",
                  },
                  url: "http://www.sos.mo.gov/elections",
                },
                {
                  id: 153,
                  lookup_tool: {
                    id: 6,
                    kind: "sample_ballot",
                    name: "Can I View my Sample Ballot?",
                  },
                  url:
                    "https://voteroutreach.sos.mo.gov/PRD/VoterOutreach/VOSearch.aspx",
                },
                {
                  id: 154,
                  lookup_tool: {
                    id: 3,
                    kind: "polling_location",
                    name: "Where is my Polling Place?",
                  },
                  url:
                    "https://voteroutreach.sos.mo.gov/PRD/VoterOutreach/VOSearch.aspx",
                },
                {
                  id: 157,
                  lookup_tool: {
                    id: 1,
                    kind: "registration_status",
                    name: "Am I Registered?",
                  },
                  url: "https://s1.sos.mo.gov/elections/voterlookup/",
                },
                {
                  id: 405,
                  lookup_tool: {
                    id: 9,
                    kind: "Overseas / Military Voter Information",
                    name: "Overseas / Military Voter Information",
                  },
                  url:
                    "https://www.sos.mo.gov/elections/goVoteMissouri/registeroverseas",
                },
                {
                  id: 406,
                  lookup_tool: {
                    id: 7,
                    kind: "State Voter Registration FAQ",
                    name: "State Voter Registration FAQ",
                  },
                  url:
                    "https://www.sos.mo.gov/elections/goVoteMissouri/votereg",
                },
              ],
              voting_methods: [
                {
                  id: 253,
                  voting_method_type: {
                    id: 3,
                    kind: "absentee_voting_with_excuse",
                    name: "Absentee Voting With Excuse",
                  },
                  allowed: true,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 254,
                  voting_method_type: {
                    id: 9,
                    kind: "overseas_absentee_voting",
                    name: "Overseas Absentee Voting",
                  },
                  allowed: true,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 255,
                  voting_method_type: {
                    id: 7,
                    kind: "all_mail_voting",
                    name: "All-Mail Voting",
                  },
                  allowed: false,
                  additional_info:
                    "In Missouri, certain elections may be held by mail.",
                  additional_info_type: "M",
                },
                {
                  id: 256,
                  voting_method_type: {
                    id: 2,
                    kind: "same_day_registration",
                    name: "Election Day (Same Day) Voter Registration",
                  },
                  allowed: false,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 257,
                  voting_method_type: {
                    id: 6,
                    kind: "in_person_absentee_voting",
                    name: "In-Person Absentee Voting",
                  },
                  allowed: true,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 258,
                  voting_method_type: {
                    id: 5,
                    kind: "early_voting",
                    name: "Early Voting",
                  },
                  allowed: false,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 259,
                  voting_method_type: {
                    id: 8,
                    kind: "provisional_voting",
                    name: "Provisional Voting",
                  },
                  allowed: true,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 260,
                  voting_method_type: {
                    id: 10,
                    kind: "military_absentee_voting",
                    name: "Military Absentee Voting",
                  },
                  allowed: true,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 261,
                  voting_method_type: {
                    id: 4,
                    kind: "absentee_voting_without_excuse",
                    name: "Absentee Voting Without Excuse",
                  },
                  allowed: false,
                  additional_info: "",
                  additional_info_type: "M",
                },
                {
                  id: 262,
                  voting_method_type: {
                    id: 1,
                    kind: "polling_place_voting",
                    name: "Polling Place Voting",
                  },
                  allowed: true,
                  additional_info: "",
                  additional_info_type: "M",
                },
              ],
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
  top: 2.8em !important;
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
