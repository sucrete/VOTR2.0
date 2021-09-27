<template>
  <div id="Resources">
    <div id="overviewNoticeWrapper">
      <div id="overviewMarquee"></div>
      <div id="overviewNotice">
        Understand your eligibility and what you need to vote.
      </div>
    </div>
    <v-tabs v-model="tab" class="knowledgeTabs" hide-slider centered>
      <v-tab :key="i">{{ i }}</v-tab>
      <v-tab :key="ii">{{ ii }}</v-tab>
      <v-tab :key="iii">{{ iii }}</v-tab>
      <v-tabs-items style="margin: 0 auto" v-model="tab">
        <v-tab-item :key="i" v-html="generalInfo"> </v-tab-item>
        <v-tab-item :key="ii" v-html="IDRequirements"> </v-tab-item>
        <v-tab-item :key="iii" v-html="eligibility"> </v-tab-item>
      </v-tabs-items>
    </v-tabs>
    <div id="resourcesSpacer"></div>
    <div id="additionalResources">
      <span class="headline"
        >Additional Resources for {{ stateName }} Voters</span
      >
      <v-list class="govResourcesList">
        <a
          class="govResourcesItem"
          :href="lilinfos.votersToolsURL"
          target="_blank"
          v-for="(lilinfos, index) in resourcesObject"
          :key="index"
        >
          <span>{{ lilinfos.votersToolsName }}</span>
        </a>
      </v-list>
    </div>
  </div>
</template>

<script>
const marked = require('marked')

export default {
  name: 'Resources',
  data() {
    return {
      tab: null,
      generalInfo:
        '<span>NO INFO</span><br><a href="/">return to landing page</a>',
      eligibility: '',
      IDRequirements: '',
      resources: '<div>nothing to see here</div>',
      i: 'General',
      ii: 'ID Requirements',
      iii: 'Eligibility',
      styleObject: {
        color: '#716E10',
      },
      voterInfoData: {
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
              short_name: 'MO',
              id: 'S29',
              name: 'Missouri',
            },
            eligibility_general_info: '',
            voting_general_info:
              '# Registration\r\n  \r\n## You can register to vote or update your registration information:\r\n  \r\n * online\r\n * by mail\r\n * in person at your elections office\r\n \r\n \r\n# Election Day Voting\r\n \r\n Polling places are open from 6am to 7pm on Election Day.\r\n \r\n## [Find my polling place](https://s1.sos.mo.gov/elections/voterlookup/)\r\n \r\n  \r\n# Early Voting\r\n \r\nYou can vote by absentee in the office of the local election authority until 5pm the night before the election. Contact your local election authority to inquire about hours and dates of operation.  \r\n\r\n \r\n# Absentee Voting\r\n\r\n## Registered voters can vote absentee if ONE of the following conditions applies: \r\n\r\n * You are absent on Election Day from the jurisdiction in which you are registered to vote \r\n * You are incapacitated or confined due to illness or physical disability, or a person who is primarily responsible for the physical care of a person who is incapacitated or confined due to illness or disability \r\n * You have religious beliefs or practices which prevent you from voting on Election Day \r\n * You are employed as an election authority, as a member of an election authority, or by an election authority at a location other than your polling place \r\n * You are incarcerated, provided all qualifications for voting are retained',
            voter_id_general_info: '',
            eligibility_requirements: [
              {
                id: 342,
                voter_type: {
                  id: 1,
                  kind: 'D',
                  name: 'Domestic Voter',
                },
                header: 'You are eligible to vote in Missouri if you:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 62,
                      kind: 'us_citizen',
                      name: 'Are a U.S citizen',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 59,
                      kind: 'state_resident',
                      name: 'Are a resident of Missouri',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 68,
                      kind: 'at_least_18_yo',
                      name: 'Are at least 18 years old by Election Day',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 343,
                voter_type: {
                  id: 1,
                  kind: 'D',
                  name: 'Domestic Voter',
                },
                header: 'You are NOT eligible to vote in Missouri if:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 1,
                items: [
                  {
                    item: {
                      id: 75,
                      kind: 'in_prison',
                      name: 'You are in prison or detention or jail or penal institution',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 74,
                      kind: 'on_parole_for_felony',
                      name: 'You are on parole for a felony conviction or convicted of a felony',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 71,
                      kind: 'convicted_of_felony',
                      name: 'You were convicted of a felony or misdemeanor connected with voting',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 344,
                voter_type: {
                  id: 1,
                  kind: 'D',
                  name: 'Domestic Voter',
                },
                header: 'You may preregister to vote in Missouri',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 3,
                items: [
                  {
                    item: {
                      id: 81,
                      kind: 'pre_register_as_of_age_17_1/2',
                      name: 'at the age of 17-1/2',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 417,
                voter_type: {
                  id: 2,
                  kind: 'O',
                  name: 'Overseas Voter',
                },
                header:
                  'U.S. citizens living abroad have the right to vote as absentee voters, provided they are eligible to vote in their state. \r\n\r\nIf you are living outside of the U.S. permanently, indefinitely, or temporarily, your voting rights stay with you, even if you never voted when you lived in the U.S.\r\n\r\nTo vote from overseas:',
                header_type: 'M',
                footer:
                  'Many states allow children who were born overseas, but never lived in the U.S., to use their U.S. parents’ last residence address to register.',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 86,
                      kind: 'complete_and_send_an_overseas_voter_registrationballot_request_form_to_your_election_office_in_the_us_this_is_one_specific_form_that_will_register_you_as_an_overseas_voter_and_request_your_absentee_ballot_simultaneously',
                      name: 'Complete and send an overseas voter registration/ballot request form to your election office in the U.S. This is one specific form that will register you as an overseas voter and request your absentee ballot – simultaneously.',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 477,
                voter_type: {
                  id: 3,
                  kind: 'M',
                  name: 'Military Voter',
                },
                header:
                  'Service members and their eligible family members living outside their voting jurisdiction (within or outside the U.S.) are able to vote as absentee voters.',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 87,
                      kind: 'if_you_are_a_service_member_or_an_eligible_family_member_there_is_a_single_form_to_file_for_both_voter_registration_and_ballot_request_it_is_often_called_the_federal_post_card_application_or_the_fpca_form_this_form_must_be_re_filed_with_your_election_office_each_time_you_change_location',
                      name: 'If you are a service member, or an eligible family member, there is a single form to file for both voter registration and ballot request. It is often called the “Federal Post Card Application” or the FPCA form. This form must be re-filed with your election office each time you change location.',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 478,
                voter_type: {
                  id: 3,
                  kind: 'M',
                  name: 'Military Voter',
                },
                header:
                  'To vote as a service member or eligible family member:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 1,
                items: [
                  {
                    item: {
                      id: 85,
                      kind: 'complete_and_send_a_voter_registrationballot_request_form_fpca_to_your_election_office_in_the_us_it_is_the_same_form_in_all_states',
                      name: 'Complete and send a voter registration/ballot request form “FPCA” to your election office in the U.S. It is the same form in all states.',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 608,
                voter_type: {
                  id: 4,
                  kind: 'Student Voter',
                  name: 'Student Eligibility',
                },
                header:
                  'If you are a student, you are eligible to vote in Missouri if:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 114,
                      kind: 'college_another_state',
                      name: 'You are attending college in another state',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 115,
                      kind: 'out_of_state_student',
                      name: 'You reside in another state but attend college in Missouri',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 123,
                      kind: 'new_student_id_from_state',
                      name: 'You provide a valid photo student ID from a college/university in Missouri at the polls',
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
                  kind: 'voter_registration',
                  name: 'Voter Registration',
                  name_format: '',
                },
                header: 'To register to vote in Missouri you should provide:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 79,
                      kind: 'the_last_four_digits_of_your_social_security_number',
                      name: 'The Last Four Digits of your Social Security Number',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 10,
                      kind: 'your_state_name_drivers_license_number',
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
                  kind: 'voter_registration',
                  name: 'Voter Registration',
                  name_format: '',
                },
                header:
                  'If you are registering to vote for the first time by mail, you will need to provide a copy of a valid ID. Acceptable forms of ID include:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 1,
                items: [
                  {
                    item: {
                      id: 72,
                      kind: 'current_and_valid_photo_id',
                      name: 'Current and Valid Photo ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 27,
                      kind: 'valid_tribal_id',
                      name: 'Valid Tribal ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 60,
                      kind: 'government_issued_document_that_shows_your_current_name_and_address',
                      name: 'Government Issued Document that shows your current name and address',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 43,
                      kind: 'utility_bill_bank_statement_government_check_or_paycheck_that_shows_your_current_name_and_address',
                      name: 'Utility Bill, Bank Statement, Government Check, or Paycheck that Shows your current name and address',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 56,
                      kind: 'birth_certificate',
                      name: 'Birth Certificate',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 65,
                      kind: 'other_proof_of_us_citizenship_issued_by_the_federal_government',
                      name: 'Other proof of US Citizenship issued by the Federal Government',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 134,
                category: {
                  id: 2,
                  kind: 'voting_in_person',
                  name: 'Voting In-Person',
                  name_format: '',
                },
                header:
                  'In Missouri, you need to show a valid ID to vote. You can use any ID from this list:',
                header_type: 'M',
                footer:
                  'If you do not have ID, you may still vote provisionally if you are registered and the signature matches.',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 171,
                      kind: 'valid_military_id',
                      name: 'Valid Military ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 98,
                      kind: 'valid_state_non_drivers_id',
                      name: "Valid <State> non-driver's ID",
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 177,
                      kind: 'valid_state_name_drivers_license',
                      name: "Valid Missouri Driver's License",
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 208,
                      kind: 'valid_student_id_from_state_school',
                      name: 'Valid Student ID from State School',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 24,
                      kind: 'bank_statement_paycheck_or_government_check',
                      name: 'Bank Statement, Paycheck or Government Check',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 115,
                      kind: 'valid_us_passport',
                      name: 'Valid US Passport',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 116,
                      kind: 'valid_military_id',
                      name: 'Valid Military ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 17,
                      kind: 'utility_bill',
                      name: 'Utility Bill',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 214,
                      kind: 'voter_registration_card',
                      name: 'Voter Registration Card',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 235,
                category: {
                  id: 3,
                  kind: 'voting_overseas',
                  name: 'Voting Overseas',
                  name_format: '',
                },
                header:
                  'U.S. citizens living overseas may register and request a ballot using the overseas voter registration/ballot request form. You will have the following identification options when completing the form:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 245,
                      kind: 'us_state_or_territory_or_district_issued_id',
                      name: 'U.S. State or Territory or District Issued ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 246,
                      kind: 'option_to_indicate_that_you_do_not_have_the_requested_id',
                      name: 'Option to Indicate that you do not have the Requested ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 243,
                      kind: 'last_4_digits_of_your_social_security_number',
                      name: 'Last 4 Digits of your Social Security Number',
                    },
                    position: 0,
                  },
                ],
              },
              {
                id: 291,
                category: {
                  id: 4,
                  kind: 'voting_military',
                  name: 'Voting Military',
                  name_format: '',
                },
                header:
                  'U.S. citizens living overseas may register and request a ballot using the overseas voter registration/ballot request form. You will have the following identification options when completing the form:\r\nService members and their dependents may register and request a ballot using the federal voter registration/ballot request form ("FPCA"). You will have the following identification options when completing the form:',
                header_type: 'M',
                footer: '',
                footer_type: 'M',
                position: 0,
                items: [
                  {
                    item: {
                      id: 245,
                      kind: 'us_state_or_territory_or_district_issued_id',
                      name: 'U.S. State or Territory or District Issued ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 246,
                      kind: 'option_to_indicate_that_you_do_not_have_the_requested_id',
                      name: 'Option to Indicate that you do not have the Requested ID',
                    },
                    position: 0,
                  },
                  {
                    item: {
                      id: 243,
                      kind: 'last_4_digits_of_your_social_security_number',
                      name: 'Last 4 Digits of your Social Security Number',
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
                  kind: 'O',
                  name: 'Overseas Voter',
                },
                additional_info:
                  'Voters who are in Federal service and are eligible to receive hostile fire, imminent danger pay, or are in a location designated as a combat zone may return their voted ballots by fax or email. \r\n\r\n(a) Members of the armed forces of the United States, while in active service, and their spouses and dependents; \r\n\r\n(b) Active members of the merchant marine of the United States and their spouses and dependents; \r\n\r\n(c) Civilian employees of the United States government working outside the boundaries of the United States, and their spouses and dependents; \r\n\r\n(d) Active members of religious or welfare organizations assisting servicemen, and their spouses and dependents; \r\n\r\n(e) Persons who have been honorably discharged from the armed forces or who have terminated their service or employment in any group mentioned in this section within sixty days of an election, and their spouses and dependents. \r\n\r\nPlease note that private email over the Internet is not a secure method of transfer for documents containing your confidential identity information. OVF strongly recommends regular mail and fax over email transfer.',
                additional_info_type: 'M',
                items: [
                  {
                    id: 2252,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2253,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2254,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2255,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2256,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2257,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2258,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2259,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2260,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2261,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2262,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2263,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2264,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2265,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2266,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2277,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2278,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2279,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2280,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2281,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                ],
              },
              {
                id: 78,
                voter_type: {
                  id: 1,
                  kind: 'D',
                  name: 'Domestic Voter',
                },
                additional_info: '',
                additional_info_type: 'M',
                items: [
                  {
                    id: 2282,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2283,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2284,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2285,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2286,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2287,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2288,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2289,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2290,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2291,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2292,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2293,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2294,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2295,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2296,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2307,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2308,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2309,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2310,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2311,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                ],
              },
              {
                id: 79,
                voter_type: {
                  id: 3,
                  kind: 'M',
                  name: 'Military Voter',
                },
                additional_info:
                  'Voters who are in Federal service and are eligible to receive hostile fire, imminent danger pay, or are in a location designated as a combat zone may return their voted ballots by fax or email. \r\n\r\n(a) Members of the armed forces of the United States, while in active service, and their spouses and dependents; \r\n\r\n(b) Active members of the merchant marine of the United States and their spouses and dependents; \r\n\r\n(c) Civilian employees of the United States government working outside the boundaries of the United States, and their spouses and dependents; \r\n\r\n(d) Active members of religious or welfare organizations assisting servicemen, and their spouses and dependents; \r\n\r\n(e) Persons who have been honorably discharged from the armed forces or who have terminated their service or employment in any group mentioned in this section within sixty days of an election, and their spouses and dependents. \r\n\r\nPlease note that private email over the Internet is not a secure method of transfer for documents containing your confidential identity information. OVF strongly recommends regular mail and fax over email transfer.',
                additional_info_type: 'M',
                items: [
                  {
                    id: 2312,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2313,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2314,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2315,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2316,
                    document_type: {
                      id: 4,
                      kind: 'blank_ballot_to_voter',
                      name: 'Blank Ballot To Voter',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2317,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2318,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2319,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2320,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2321,
                    document_type: {
                      id: 2,
                      kind: 'absentee_ballot_request',
                      name: 'Absentee Ballot Request',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2322,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2323,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2324,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2325,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2326,
                    document_type: {
                      id: 3,
                      kind: 'voted_absentee_ballot_return',
                      name: 'Voted-Absentee Ballot Return',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2337,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 1,
                      kind: 'in_person',
                      name: 'In-Person',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2338,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 2,
                      kind: 'mail',
                      name: 'Mail',
                    },
                    allowed: true,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2339,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 4,
                      kind: 'fax',
                      name: 'Fax',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2340,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 3,
                      kind: 'email',
                      name: 'Email',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                  {
                    id: 2341,
                    document_type: {
                      id: 1,
                      kind: 'voter_registration',
                      name: 'Voter Registration',
                    },
                    document_transmission_method: {
                      id: 5,
                      kind: 'online',
                      name: 'Online',
                    },
                    allowed: false,
                    additional_info: '',
                    additional_info_type: 'M',
                  },
                ],
              },
            ],
            lookup_tools: [
              {
                id: 152,
                lookup_tool: {
                  id: 5,
                  kind: 'election_information',
                  name: 'State Elections Website',
                },
                url: 'http://www.sos.mo.gov/elections',
              },
              {
                id: 153,
                lookup_tool: {
                  id: 6,
                  kind: 'sample_ballot',
                  name: 'Can I View my Sample Ballot?',
                },
                url: 'https://voteroutreach.sos.mo.gov/PRD/VoterOutreach/VOSearch.aspx',
              },
              {
                id: 154,
                lookup_tool: {
                  id: 3,
                  kind: 'polling_location',
                  name: 'Where is my Polling Place?',
                },
                url: 'https://voteroutreach.sos.mo.gov/PRD/VoterOutreach/VOSearch.aspx',
              },
              {
                id: 157,
                lookup_tool: {
                  id: 1,
                  kind: 'registration_status',
                  name: 'Am I Registered?',
                },
                url: 'https://s1.sos.mo.gov/elections/voterlookup/',
              },
              {
                id: 405,
                lookup_tool: {
                  id: 9,
                  kind: 'Overseas / Military Voter Information',
                  name: 'Overseas / Military Voter Information',
                },
                url: 'https://www.sos.mo.gov/elections/goVoteMissouri/registeroverseas',
              },
              {
                id: 406,
                lookup_tool: {
                  id: 7,
                  kind: 'State Voter Registration FAQ',
                  name: 'State Voter Registration FAQ',
                },
                url: 'https://www.sos.mo.gov/elections/goVoteMissouri/votereg',
              },
            ],
            voting_methods: [
              {
                id: 253,
                voting_method_type: {
                  id: 3,
                  kind: 'absentee_voting_with_excuse',
                  name: 'Absentee Voting With Excuse',
                },
                allowed: true,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 254,
                voting_method_type: {
                  id: 9,
                  kind: 'overseas_absentee_voting',
                  name: 'Overseas Absentee Voting',
                },
                allowed: true,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 255,
                voting_method_type: {
                  id: 7,
                  kind: 'all_mail_voting',
                  name: 'All-Mail Voting',
                },
                allowed: false,
                additional_info:
                  'In Missouri, certain elections may be held by mail.',
                additional_info_type: 'M',
              },
              {
                id: 256,
                voting_method_type: {
                  id: 2,
                  kind: 'same_day_registration',
                  name: 'Election Day (Same Day) Voter Registration',
                },
                allowed: false,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 257,
                voting_method_type: {
                  id: 6,
                  kind: 'in_person_absentee_voting',
                  name: 'In-Person Absentee Voting',
                },
                allowed: true,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 258,
                voting_method_type: {
                  id: 5,
                  kind: 'early_voting',
                  name: 'Early Voting',
                },
                allowed: false,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 259,
                voting_method_type: {
                  id: 8,
                  kind: 'provisional_voting',
                  name: 'Provisional Voting',
                },
                allowed: true,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 260,
                voting_method_type: {
                  id: 10,
                  kind: 'military_absentee_voting',
                  name: 'Military Absentee Voting',
                },
                allowed: true,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 261,
                voting_method_type: {
                  id: 4,
                  kind: 'absentee_voting_without_excuse',
                  name: 'Absentee Voting Without Excuse',
                },
                allowed: false,
                additional_info: '',
                additional_info_type: 'M',
              },
              {
                id: 262,
                voting_method_type: {
                  id: 1,
                  kind: 'polling_place_voting',
                  name: 'Polling Place Voting',
                },
                allowed: true,
                additional_info: '',
                additional_info_type: 'M',
              },
            ],
          },
        ],
      },
      resourcesObject: [],
      dummyresourcesObject: [
        {
          votersToolsName: 'State Elections Website',
          votersToolsURL: 'http://www.elections.ny.gov/INDEX.html',
        },
        {
          votersToolsName: 'Where is my Polling Place?',
          votersToolsURL:
            'https://voterlookup.elections.state.ny.us/votersearch.aspx',
        },
        {
          votersToolsName: 'Can I Register to Vote Online?',
          votersToolsURL:
            'https://dmv.ny.gov/more-info/electronic-voter-registration-application',
        },
        {
          votersToolsName: 'Am I Registered?',
          votersToolsURL: 'https://voterlookup.elections.state.ny.us/',
        },
        {
          votersToolsName: 'Overseas / Military Voter Information',
          votersToolsURL: 'http://www.elections.ny.gov/VotingMilitaryFed.html',
        },
        {
          votersToolsName: 'State Voter Registration FAQ',
          votersToolsURL: 'http://www.elections.ny.gov/FAQ.html',
        },
      ],
      stateName: 'New York',
    }
  },
  mounted() {
    this.fillItUp()
    console.log('beef eater')
    // this.$nextTick(function () {
    //   this.insertIcon()
    // })
  },
  methods: {
    makeActive: (item) => {
      this.active = item
    },
    capitalizeIt(string) {
      return string.charAt(0).toUpperCase() + string.slice(1)
    },
    fillItUp() {
      console.log('🦍🦍🦍🦍🦍🦍🦍🦍 WORKING 🦍🦍🦍🦍🦍🦍🦍🦍')
      // const voterInfo = this.$store.getters.getVoterInfo.objects[0]
      const voterInfo = this.voterInfoData.objects[0]
      const generalInfo = voterInfo.voting_general_info
      this.generalInfo = marked(generalInfo)
      this.stateName = voterInfo.state.name
      console.log('🦍🦍🦍🦍🦍🦍🦍🦍 WORKING 🦍🦍🦍🦍🦍🦍🦍🦍')
      voterInfo.eligibility_requirements.forEach((headly) => {
        this.eligibility +=
          '<span class="happiHeader">' + headly.header + '</span> <ul>'
        headly.items.forEach((itemys) => {
          // removed capitalizeIt from itemys.item.name below e.g. "this.capitalizeIt(itemys.item.name)" (between the '<li>' tags)
          this.eligibility +=
            '<li>' + this.capitalizeIt(itemys.item.name) + '</li>'
        })
        this.eligibility += '</ul>'
        // Object.prototype.hasOwnProperty.call(divs[keys[ttt]], 'officeIndices')
        if (Object.prototype.hasOwnProperty.call(headly, 'footer')) {
          this.eligibility +=
            '<p id="resourcesFooter"><em>' + headly.footer + '</em></p>'
        }
      })
      voterInfo.identification_requirements.forEach((credly) => {
        this.IDRequirements +=
          '<span class="happiHeader">' + credly.header + '</span> <ul>'
        credly.items.forEach((itemysis) => {
          // removed capitalizeIt from itemysis.item.name below e.g. "this.capitalizeIt(itemysis.item.name)" (between the '<li>' tags)
          this.IDRequirements +=
            '<li>' + this.capitalizeIt(itemysis.item.name) + '</li>'
        })
        this.IDRequirements += '</ul>'
        if (Object.prototype.hasOwnProperty.call(credly, 'footer')) {
          this.IDRequirements +=
            '<p id="resourcesFooter"><em>' + credly.footer + '</em></p>'
        }
      })
      voterInfo.lookup_tools.forEach((tooly) => {
        const tableElementsKeeper = {}
        tableElementsKeeper.votersToolsName = tooly.lookup_tool.name
        tableElementsKeeper.votersToolsURL = tooly.url
        this.resourcesObject.push(tableElementsKeeper)
      })
    },
    insertIcon() {
      const ourHeading = document.getElementById('find-my-polling-place')
      const aLink = ourHeading.childNodes[0]
      const ourLink = aLink.getAttribute('href')
      const iconHTML =
        '<i aria-hidden="true" class="v-icon material-icons" style="color: white; font-size: 18px;">place</i>'
      const buttonHTML =
        '<form action="' +
        ourLink +
        '" method="get" target="_blank"><button id="find-my-trolling-place"> ' +
        iconHTML +
        ' Find My Polling Place </button></form>'
      ourHeading.insertAdjacentHTML('beforebegin', buttonHTML)
      ourHeading.parentNode.removeChild(ourHeading)
    },
    convertNewLines(str) {
      const flippedstring = str.split('\r\n').join('<br />')
      return flippedstring
    },
  },
}
</script>

<style>
.headline {
  font-family: 'Roboto', sans-serif;
  font-weight: 500 !important;
}

#find-my-trolling-place {
  background-color: #ff9800;
  color: white !important;
  width: 95%;
  will-change: box-shadow;
  box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
    0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);
  align-items: center;
  border-radius: 2px;
  display: inline-flex;
  height: 36px;
  flex: 0 0 auto;
  font-size: 16px;
  font-weight: 500;
  justify-content: center;
  margin: 6px 8px;
  min-width: 88px;
  outline: 0;
  text-transform: uppercase;
  text-decoration: none;
  transition: 0.3s cubic-bezier(0.25, 0.8, 0.5, 1), color 1ms;
  position: relative;
  vertical-align: middle;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
#additionalResources {
  background-color: #f7f7f7;
  /* position: absolute; */
  min-height: 10em;
  width: 97%;
  bottom: 0px;
  color: #3e3830;
  margin: 0 auto;
  margin-bottom: 10px;
  padding: 25px;
  border-radius: 3px;
  display: block;
}
/* the toolkit tabs container */
.v-tabs.knowledgeTabs .v-tabs__bar.theme--light .v-tabs__wrapper {
  box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2),
    0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12);
  margin-top: 1.5em;
  margin-bottom: 2em;
  border-radius: 2px;
  height: 36px;
  text-align: left;
}

.v-tabs.knowledgeTabs {
  /* width: 21.1em; */
}
.v-tabs.knowledgeTabs .v-window {
  font-family: 'Roboto', sans-serif;
  position: relative;
  width: 34em;
  line-height: 1.444444;
  font-size: 16px;
  font-style: normal;
  padding-top: 1.5rem;
  padding-bottom: 2rem;
}
.v-tabs.knowledgeTabs .v-window > * {
  text-align: left;
}
/* the individual tabs */
.v-tabs.knowledgeTabs
  .v-tabs__bar.theme--light
  .v-tabs__wrapper
  .v-tabs__container.v-tabs__container--centered
  .v-tabs__div
  .v-tabs__item {
  color: rgb(54, 54, 54) !important;
  font-family: 'Roboto', sans-serif;
  font-weight: 500;
  letter-spacing: 0em;
  font-size: 14px;
  padding: 6px 7px;
}
.v-tabs.knowledgeTabs
  .v-tabs__bar.theme--light
  .v-tabs__wrapper
  .v-tabs__container.v-tabs__container--centered
  .v-tabs__div {
  height: 36px;
  margin-left: 0;
  margin-right: 0;
}
/* inactive tabs are a given lighter text */
.v-tabs.knowledgeTabs
  .v-tabs__bar.theme--light
  .v-tabs__wrapper
  .v-tabs__container.v-tabs__container--centered
  .v-tabs__div
  .v-tabs__item:not(.v-tabs__item--active) {
  color: rgb(174, 174, 174) !important;
}
.v-tabs.knowledgeTabs
  .v-tabs__bar.theme--light
  .v-tabs__wrapper
  .v-tabs__container.v-tabs__container--centered
  .v-tabs__div
  .v-tabs__item:not(.v-tabs__item--active):hover {
  color: rgb(124, 124, 124) !important;
  background-color: rgb(230, 230, 230) !important;
}
.v-tabs.knowledgeTabs
  .v-tabs__bar.theme--light
  .v-tabs__wrapper
  .v-tabs__container.v-tabs__container--centered
  .v-tabs__div
  .v-tabs__item.v-tabs__item--active {
  background-color: rgb(229, 229, 229);
}
.v-window-item h1 {
  font-size: 1.3em;
  font-weight: 700;
  color: black;
}
.v-window-item h2 {
  font-weight: 500;
  font-size: 16px;
}
.v-tabs.knowledgeTabs
  .v-window
  .v-window__container.v-window__container--is-active {
  min-height: 55em !important;
}
.v-tabs__container.v-tabs__container--centered.v-tabs__container--overflow {
  transform: translateX(0px) !important;
}
.tabItem {
  position: relative;
  cursor: pointer;
}
.govResourcesList {
  background-color: transparent !important;
  font-family: 'Roboto', sans-serif;
  padding: 0px 16px 16px 16px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.govResourcesItem {
  flex-basis: 30%;
  background-color: #fff;
  border-radius: 7px;

  text-align: center;
  height: 120px;
  margin-top: 5%;
  position: relative;
  transition: 0.3s all ease;
  border: 1px solid #1b77d250;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.01), 0 2px 2px rgba(0, 0, 0, 0.02),
    0 4px 4px rgba(0, 0, 0, 0.03), 0 8px 8px rgba(0, 0, 0, 0.04);
}
.govResourcesItem:hover {
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.01), 0 2px 2px rgba(0, 0, 0, 0.02),
    0 4px 4px rgba(0, 0, 0, 0.03), 0 8px 8px rgba(0, 0, 0, 0.04),
    0 16px 16px rgba(0, 0, 0, 0.05);
  /* outline: 2px solid #6d7dad49;
  outline-offset: -10px; */
}
.govResourcesItem:hover span {
  color: #1b76d2;
}
.govResourcesItem:visited {
  color: #1b76d2;
}
.govResourcesItem span {
  position: absolute;
  transition: 0.3s all ease;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-weight: 500;
  color: #1b76d2;
}
ul {
  margin: 0;
}
ul {
  list-style-type: none;
}
ul > li {
  list-style-type: none;
  text-indent: -0.5em;
  padding-inline-start: 3px;
}
li:before {
  content: '· ';
}
.happiHeader {
  margin-bottom: 1em;
  font-family: 'Roboto', sans-serif;
  font-weight: 500;
}
/* .happiHeader:first-of-type {
  margin-top: 0px !important;
} */
em {
  color: grey;
}
#find-my-trolling-place i {
  padding-right: 0.3em;
}
@media screen and (max-width: 321px) {
  .v-tabs.knowledgeTabs .v-window {
    left: 0em !important;
  }
}
@media screen and (max-width: 750px) {
  #additionalResources {
    width: 95%;
    margin-bottom: 20px;
  }
  .v-tabs.knowledgeTabs .v-window {
    width: 90vw;
  }
}
@media screen and (min-width: 430px) and (max-width: 470px) {
  .v-tabs.knowledgeTabs .v-window {
  }
}
@media screen and (min-width: 470px) and (max-width: 500px) {
  .v-tabs.knowledgeTabs .v-window {
  }
}
@media screen and (min-width: 500px) and (max-width: 550px) {
  .v-tabs.knowledgeTabs .v-window {
  }
}
@media screen and (min-width: 550px) and (max-width: 580px) {
  .v-tabs.knowledgeTabs .v-window {
  }
}
@media screen and (min-width: 580px) and (max-width: 650px) {
  .v-tabs.knowledgeTabs .v-window {
  }
}
@media screen and (min-width: 650px) and (max-width: 700px) {
  .v-tabs.knowledgeTabs .v-window {
  }
}
@media screen and (max-width: 750px) {
  #Resources
    .v-tabs.knowledgeTabs
    .v-item-group
    .v-slide-group__wrapper
    .v-slide-group__content
    .v-tab {
    padding-left: 16px;
    padding-right: 16px;
  }
}
@media screen and (min-width: 375px) and (max-width: 503px) {
  button#find-my-trolling-place {
    width: 90%;
    left: 2.5%;
  }
}
@media screen and (max-width: 700px) {
  .v-tabs.knowledgeTabs {
  }
}
@media screen and (min-width: 413px) and (max-width: 432px) {
  .v-tabs.knowledgeTabs .v-window {
    width: 90vw;
    left: -2.2em;
  }
}
@media only screen and (max-width: 375px) {
  button#find-my-trolling-place {
    width: 90%;
    left: 2.5%;
  }
  .v-tabs.knowledgeTabs .v-window {
    width: 90vw;
    left: -1.5em;
  }
  #additionalResources {
    width: 95%;
  }
}
</style>
