<template>
  <div class="Officials">
    <div id="overviewNoticeWrapper">
      <div id="overviewMarquee"></div>
      <div id="overviewNotice">Meet your elected officials.</div>
    </div>

    <div class="hotBod">
      <div id="officialsBody">
        <!-- NEW CONTAINER FOR CREATING CARDS BELOW -->

        <div v-for="(item, index) in divisionsAndOfficials" :key="index">
          <div class="sectionHeader">
            {{ item.division }}
          </div>
          <v-container fluid grid-list-lg>
            <v-layout row wrap>
              <v-flex
                xs12
                sm6
                md6
                class="cardWrapperFlex"
                v-for="(rep, index) in item.representatives"
                :key="index"
              >
                <v-hover>
                  <v-card
                    color="white"
                    class="mb-2 pb-0"
                    :class="`elevation-${rep.show ? 5 : 2}`"
                  >
                    <div class="d-flex flex-no-wrap justify-space-between">
                      <div>
                        <v-card-title v-text="rep.repName"></v-card-title>

                        <v-card-subtitle
                          v-text="rep.repTitle"
                        ></v-card-subtitle>
                      </div>

                      <v-avatar class="ma-3" size="125" tile>
                        <v-img :src="rep.repPhotoURL"></v-img>
                      </v-avatar>
                    </div>

                    <v-card-actions class="pt-0 mt-2">
                      <div v-if="rep.website" class="text-xs-center">
                        <a :href="rep.website" target="_blank"
                          ><v-btn
                            depressed
                            rounded
                            small
                            outlined
                            class="repButton ml-1"
                            >Website</v-btn
                          ></a
                        >
                      </div>
                      <v-spacer></v-spacer>
                      <v-btn
                        class="infoButton mr-1"
                        v-if="
                          rep.phone ||
                          rep.addressLine1 ||
                          rep.addressLine2 ||
                          rep.channels[0]
                        "
                        icon
                        @click="rep.show = !rep.show"
                      >
                        <v-icon style="font-size: 1.3em">{{
                          show ? 'mdi-chevron-up' : 'mdi-chevron-down'
                        }}</v-icon>
                      </v-btn>
                    </v-card-actions>

                    <v-slide-y-transition
                      v-if="
                        rep.phone ||
                        rep.addressLine1 ||
                        rep.addressLine2 ||
                        rep.channels[0]
                      "
                    >
                      <v-card-text
                        class="text-xs-left repInfo"
                        v-show="rep.show"
                      >
                        {{ rep.addressLine1 }} <br />
                        {{ rep.addressLine2 }} <br />
                        <br />
                        {{ rep.phone }}
                      </v-card-text>
                    </v-slide-y-transition>
                  </v-card>
                </v-hover>
              </v-flex>
            </v-layout>
          </v-container>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Officials',
  data() {
    return {
      // googleState: this.$store.getters.showMeDatState.googleResponse,
      googleResponse: {
        data: {
          normalizedInput: {
            line1: '4153 Mercier Street',
            city: 'Kansas City',
            state: 'MO',
            zip: '64112',
          },
          kind: 'civicinfo#representativeInfoResponse',
          divisions: {
            'ocd-division/country:us/state:mo': {
              name: 'Missouri',
              officeIndices: [2, 4, 5, 6, 7, 8, 9, 10],
            },
            'ocd-division/country:us/state:mo/cd:5': {
              name: "Missouri's 5th congressional district",
              officeIndices: [3],
            },
            'ocd-division/country:us': {
              name: 'United States',
              officeIndices: [0, 1],
            },
            'ocd-division/country:us/state:mo/county:jackson': {
              name: 'Jackson County',
              officeIndices: [11, 12, 13, 14],
            },
          },
          offices: [
            {
              name: 'President of the United States',
              divisionId: 'ocd-division/country:us',
              levels: ['country'],
              roles: ['headOfState', 'headOfGovernment'],
              officialIndices: [0],
            },
            {
              name: 'Vice President of the United States',
              divisionId: 'ocd-division/country:us',
              levels: ['country'],
              roles: ['deputyHeadOfGovernment'],
              officialIndices: [1],
            },
            {
              name: 'U.S. Senator',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['country'],
              roles: ['legislatorUpperBody'],
              officialIndices: [2, 3],
            },
            {
              name: 'U.S. Representative',
              divisionId: 'ocd-division/country:us/state:mo/cd:5',
              levels: ['country'],
              roles: ['legislatorLowerBody'],
              officialIndices: [4],
            },
            {
              name: 'Governor of Missouri',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              roles: ['headOfGovernment'],
              officialIndices: [5],
            },
            {
              name: 'Lieutenant Governor of Missouri',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              roles: ['deputyHeadOfGovernment'],
              officialIndices: [6],
            },
            {
              name: 'MO Secretary of State',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              officialIndices: [7],
            },
            {
              name: 'MO State Treasurer',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              officialIndices: [8],
            },
            {
              name: 'MO Attorney General',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              officialIndices: [9],
            },
            {
              name: 'MO Supreme Court Judge',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              officialIndices: [10, 11, 12, 13, 14, 15, 16],
            },
            {
              name: 'MO State Auditor',
              divisionId: 'ocd-division/country:us/state:mo',
              levels: ['administrativeArea1'],
              officialIndices: [17],
            },
            {
              name: 'Jackson County Sheriff',
              divisionId: 'ocd-division/country:us/state:mo/county:jackson',
              levels: ['administrativeArea2'],
              officialIndices: [18],
            },
            {
              name: 'Jackson County Prosecuting Attorney',
              divisionId: 'ocd-division/country:us/state:mo/county:jackson',
              levels: ['administrativeArea2'],
              officialIndices: [19],
            },
            {
              name: 'Jackson County Executive',
              divisionId: 'ocd-division/country:us/state:mo/county:jackson',
              levels: ['administrativeArea2'],
              officialIndices: [20],
            },
            {
              name: 'Jackson County Legislator',
              divisionId: 'ocd-division/country:us/state:mo/county:jackson',
              levels: ['administrativeArea2'],
              officialIndices: [21, 22, 23],
            },
          ],
          officials: [
            {
              name: 'Donald J. Trump',
              address: [
                {
                  line1: '1600 Pennsylvania Avenue Northwest',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20500',
                },
              ],
              party: 'Republican Party',
              phones: ['(202) 456-1111'],
              urls: ['https://www.whitehouse.gov/'],
              photoUrl:
                'https://www.whitehouse.gov/sites/whitehouse.gov/files/images/45/PE%20Color.jpg',
              channels: [
                {
                  type: 'Facebook',
                  id: 'DonaldTrump',
                },
                {
                  type: 'Twitter',
                  id: 'potus',
                },
                {
                  type: 'YouTube',
                  id: 'whitehouse',
                },
              ],
            },
            {
              name: 'Mike Pence',
              address: [
                {
                  line1: '1600 Pennsylvania Avenue Northwest',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20500',
                },
              ],
              party: 'Republican Party',
              phones: ['(202) 456-1111'],
              urls: ['https://www.whitehouse.gov/'],
              photoUrl:
                'https://www.whitehouse.gov/sites/whitehouse.gov/files/images/45/VPE%20Color.jpg',
              channels: [
                {
                  type: 'Facebook',
                  id: 'mikepence',
                },
                {
                  type: 'Twitter',
                  id: 'VP',
                },
              ],
            },
            {
              name: 'Roy Blunt',
              address: [
                {
                  line1: '260 Russell Senate Office Building',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20510',
                },
              ],
              party: 'Republican Party',
              phones: ['(202) 224-5721'],
              urls: ['https://www.blunt.senate.gov/'],
              photoUrl:
                'http://bioguide.congress.gov/bioguide/photo/B/B000575.jpg',
              channels: [
                {
                  type: 'Facebook',
                  id: 'SenatorBlunt',
                },
                {
                  type: 'Twitter',
                  id: 'RoyBlunt',
                },
                {
                  type: 'YouTube',
                  id: 'SenatorBlunt',
                },
                {
                  type: 'YouTube',
                  id: 'BluntforSenate2010',
                },
              ],
            },
            {
              name: 'Josh Hawley',
              address: [
                {
                  line1: '212 Russell Senate Office Building',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20510',
                },
              ],
              party: 'Republican Party',
              phones: ['(202) 224-6154'],
              urls: ['https://www.hawley.senate.gov/'],
              emails: ['senator@hawley.senate.gov'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'SenatorHawley',
                },
                {
                  type: 'Twitter',
                  id: 'SenHawleyPress',
                },
              ],
            },
            {
              name: 'Emanuel Cleaver',
              address: [
                {
                  line1: '2335 Rayburn House Office Building',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20515',
                },
              ],
              party: 'Democratic Party',
              phones: ['(202) 225-4535'],
              urls: ['https://cleaver.house.gov/'],
              photoUrl:
                'http://bioguide.congress.gov/bioguide/photo/C/C001061.jpg',
              channels: [
                {
                  type: 'Facebook',
                  id: 'emanuelcleaverii',
                },
                {
                  type: 'Twitter',
                  id: 'repcleaver',
                },
                {
                  type: 'YouTube',
                  id: 'repcleaver',
                },
              ],
            },
            {
              name: 'Michael L. Parson',
              address: [
                {
                  line1: 'State Capitol Building',
                  line2: '201 West Capitol Avenue',
                  line3: 'Room 224',
                  city: 'Jefferson City',
                  state: 'MO',
                  zip: '65101',
                },
              ],
              party: 'Republican Party',
              phones: ['(573) 751-3222'],
              urls: ['https://governor.mo.gov/'],
              photoUrl:
                'https://ltgov.mo.gov/wp-content/uploads/2017/01/Parson-headshot.jpg',
              emails: ['ltgovinfo@ltgov.mo.gov'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'GovMikeParson',
                },
                {
                  type: 'Twitter',
                  id: 'GovParsonMO',
                },
              ],
            },
            {
              name: 'Mike Kehoe',
              address: [
                {
                  line1: '201 West Capitol Avenue',
                  city: 'Jefferson City',
                  state: 'MO',
                  zip: '65101',
                },
              ],
              party: 'Republican Party',
              phones: ['(573) 751-4727'],
              urls: ['https://ltgov.mo.gov/'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'MoLtGovMikeKehoe',
                },
                {
                  type: 'Twitter',
                  id: 'LtGovMikeKehoe',
                },
              ],
            },
            {
              name: 'John R. Ashcroft',
              address: [
                {
                  line1: '201 West Capitol Avenue',
                  city: 'Jefferson City',
                  state: 'MO',
                  zip: '65101',
                },
              ],
              party: 'Republican Party',
              phones: ['(573) 751-4936'],
              urls: ['https://www.sos.mo.gov/'],
              emails: ['info@sos.mo.gov'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'MissouriSOS',
                },
                {
                  type: 'Twitter',
                  id: 'MissouriSOS',
                },
              ],
            },
            {
              name: 'Scott Fitzpatrick',
              party: 'Republican Party',
              phones: ['(573) 751-8533'],
              urls: ['https://www.treasurer.mo.gov/'],
              emails: ['info@treasurer.mo.gov'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'MOTreasurer',
                },
                {
                  type: 'Twitter',
                  id: 'MOTreasurer',
                },
              ],
            },
            {
              name: 'Eric Schmitt',
              party: 'Republican Party',
              phones: ['(573) 751-3321'],
              urls: ['https://www.ago.mo.gov/'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'AttorneyGeneralSchmitt',
                },
                {
                  type: 'Twitter',
                  id: 'AGEricSchmitt',
                },
              ],
            },
            {
              name: 'George W. Draper, III',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Patricia Breckenridge',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Paul C. Wilson',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Zel M. Fischer',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Laura Denvir Stith',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Mary R. Russell',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'W. Brent Powell',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Nicole Galloway',
              party: 'Democratic Party',
              phones: ['(800) 347-8597'],
              urls: ['https://auditor.mo.gov/'],
              emails: ['moaudit@auditor.mo.gov'],
              channels: [
                {
                  type: 'Facebook',
                  id: 'NicoleGallowayCPA',
                },
                {
                  type: 'Twitter',
                  id: 'AuditorGalloway',
                },
              ],
            },
            {
              name: 'Darryl Forte',
              address: [
                {
                  line1: '4001 Northeast Lakewood Court',
                  city: "Lee's Summit",
                  state: 'MO',
                  zip: '64064',
                },
              ],
              party: 'Democratic',
              phones: ['(816) 541-1969'],
              urls: ['https://www.jacksoncountysheriff.org/'],
              emails: ['sheriff@jacksongov.org'],
            },
            {
              name: 'Jean Peters Baker',
              address: [
                {
                  line1: '415 East 12th Street',
                  city: 'Kansas City',
                  state: 'MO',
                  zip: '64106',
                },
              ],
              party: 'Democratic',
              phones: ['(816) 881-3555'],
              urls: ['https://www.jacksoncountyprosecutor.com/'],
            },
            {
              name: 'Frank White, Jr.',
              address: [
                {
                  line1: '415',
                  line2: '200 East 12th Street',
                  city: 'Kansas City',
                  state: 'MO',
                  zip: '64106',
                },
              ],
              party: 'Democratic',
              phones: ['(816) 881-3333'],
              urls: ['http://www.jacksongov.org/395/County-Executive'],
              emails: ['mhennosy@jacksongov.org'],
            },
            {
              name: 'Crystal Williams',
              address: [
                {
                  line1: '415 East 12th Street',
                  city: 'Kansas City',
                  state: 'MO',
                  zip: '64106',
                },
              ],
              party: 'Democratic',
              phones: ['(816) 881-3464'],
              urls: [
                'https://www.jacksongov.org/704/2nd-District-At-Large-Crystal-Williams',
              ],
              emails: ['crystalwilliams@jacksongov.org'],
            },
            {
              name: 'Tony Miller',
              address: [
                {
                  line1: '201 West Lexington Avenue',
                  city: 'Independence',
                  state: 'MO',
                  zip: '64050',
                },
              ],
              party: 'Unknown',
              phones: ['(816) 881-4423'],
              urls: [
                'https://www.jacksongov.org/705/3rd-District-At-Large-Tony-Miller',
              ],
              emails: ['tmiller@jacksongov.org'],
            },
            {
              name: 'Jalen Anderson',
              address: [
                {
                  line1: '415',
                  line2: '201 East 12th Street',
                  city: 'Kansas City',
                  state: 'MO',
                  zip: '64106',
                },
              ],
              party: 'Democratic',
              phones: ['(816) 881-4477'],
              urls: [
                'https://www.jacksongov.org/1077/1st-District-At-Large-Jalen-Anderson',
              ],
              emails: ['JAnderson@jacksongov.org'],
            },
          ],
        },
        status: 200,
        statusText: '',
        headers: {
          'cache-control': 'private',
          'content-encoding': 'gzip',
          'content-length': '2234',
          'content-type': 'application/json; charset=UTF-8',
          date: 'Sun, 30 Aug 2020 05:27:10 GMT',
          server: 'ESF',
        },
        config: {
          transformRequest: {},
          transformResponse: {},
          timeout: 0,
          xsrfCookieName: 'XSRF-TOKEN',
          xsrfHeaderName: 'X-XSRF-TOKEN',
          maxContentLength: -1,
          headers: {
            Accept: 'application/json, text/plain, */*',
          },
          method: 'get',
          url: 'https://www.googleapis.com/civicinfo/v2/representatives?key=AIzaSyBY3zNf2iIVGQWmoRPHNgObx4PnWT4-cqE&address=4153+Mercier+Street%2C+Kansas+City%2C+Missouri+64112',
        },
        request: {},
      },
      divisionKeys: [],
      divisionsAndOfficials: [],
      phoneIconURL: 'https://i.imgur.com/kXKmZrE.png',
      linkIconURL: 'https://i.imgur.com/7O903TX.png',
      locationIconURL: 'https://i.imgur.com/6rxdk4T.png',
      show: false,
      show2: false,
    }
  },
  methods: {
    toTitleCase(str) {
      // credit for toTitleCase() -> https://stackoverflow.com/questions/196972/convert-string-to-title-case-with-javascript/196991#196991
      return str.replace(/\w\S*/g, function (txt) {
        return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase()
      })
    },
    importData() {
      console.log('importData() fired')
      const divisions = this.googleResponse.data.divisions
      let divisionQuays = []
      divisionQuays = Object.getOwnPropertyNames(divisions)
      const storer = []
      // reversing the division keys and removing the "obj" add-on
      for (let i = divisionQuays.length - 1; i >= 0; i--) {
        storer.push(divisionQuays[i])
      }
      storer.shift()
      this.divisionKeys = storer
    },
    dataShaker() {
      const GState = this.googleResponse
      const divs = GState.data.divisions
      const keys = this.divisionKeys
      console.log('dataShaker() fired')
      for (let ttt = 0; ttt < keys.length; ttt++) {
        if (
          Object.prototype.hasOwnProperty.call(divs[keys[ttt]], 'officeIndices')
        ) {
          let upperCasedDivisionName1 = this.toTitleCase(divs[keys[ttt]].name)
          if (upperCasedDivisionName1.endsWith('City')) {
            const upperCasedDivisionNameArray1 =
              upperCasedDivisionName1.split(' ')
            upperCasedDivisionNameArray1.pop()
            upperCasedDivisionName1 =
              'City of ' + upperCasedDivisionNameArray1.join(' ')
          }
          const superSaver = {}
          superSaver.division = upperCasedDivisionName1
          superSaver.representatives = []
          divs[keys[ttt]].officeIndices.forEach((thing1) => {
            const GOffice1 = GState.data.offices[thing1]
            // below is the biodata for each representative using GOffice indices on GState.data e.g. GState.data.officials[GOffice1.officialIndices[1]]
            GOffice1.officialIndices.forEach((corazon) => {
              const officialObject1 = {}
              officialObject1.index = corazon
              officialObject1.show = false
              officialObject1.repTitle = GOffice1.name
              officialObject1.repName = GState.data.officials[corazon].name
              officialObject1.repPhotoURL =
                GState.data.officials[corazon].photoUrl ||
                'https://avatarairlines.com/wp-content/uploads/2020/05/Male-placeholder.jpeg'
              if (corazon === 0) {
                officialObject1.repPhotoURL =
                  'http://i.dailymail.co.uk/i/pix/2017/10/31/14/45DEE46500000578-5035763-image-m-11_1509461782123.jpg'
              } else if (corazon === 1) {
                officialObject1.repPhotoURL =
                  'http://i.dailymail.co.uk/i/pix/2017/10/31/14/45DE40EA00000578-5035763-image-a-10_1509461772135.jpg'
              }
              const theOfficial = GState.data.officials[corazon]
              officialObject1.party = theOfficial.party
              if (theOfficial.address !== undefined) {
                const _oa = theOfficial.address[0]
                officialObject1.addressLine1 = _oa.line2
                officialObject1.addressLine2 =
                  _oa.city + ', ' + _oa.state + ' ' + _oa.zip
              }
              if (theOfficial.phones !== undefined) {
                officialObject1.phone = theOfficial.phones[0]
              } else {
                officialObject1.phone = null
              }
              if (theOfficial.urls !== undefined) {
                officialObject1.website = theOfficial.urls[0]
              } else {
                officialObject1.website = null
              }
              officialObject1.channels = []
              if (!(theOfficial.channels === undefined)) {
                theOfficial.channels.forEach((Chanel) => {
                  const channelKeep = {}
                  channelKeep.channelIcon = ''
                  channelKeep.channelLink = ''
                  if (!(Chanel.type === 'GooglePlus')) {
                    if (Chanel.type === 'YouTube') {
                      channelKeep.channelLink =
                        'http://www.youtube.com/' + Chanel.id
                      channelKeep.channelIcon =
                        'https://i.imgur.com/b4J5pf1.png'
                    } else if (Chanel.type === 'Facebook') {
                      channelKeep.channelLink =
                        'http://www.facebook.com/' + Chanel.id
                      channelKeep.channelIcon =
                        'https://i.imgur.com/MvZ9x3Z.png'
                    } else if (Chanel.type === 'Twitter') {
                      channelKeep.channelLink =
                        'http://www.twitter.com/' + Chanel.id
                      channelKeep.channelIcon =
                        'https://i.imgur.com/ZnowWs0.png'
                    }
                  }
                  officialObject1.channels.push(channelKeep)
                })
              }
              // complete push for an individual representative below
              superSaver.representatives.push(officialObject1)
            })
          })
          this.divisionsAndOfficials.push(superSaver)
        }
      }
      // console.log('📛📛📛 ➖➖➖➖➖➖➖➖ all rep info ➖➖➖➖➖➖➖➖  📛📛📛' + '\n' + JSON.stringify(this.divisionsAndOfficials, null, '\t'))
    },
  },
  beforeMount() {
    this.importData()
    this.dataShaker()
  },
}
</script>

<style >
#officialsBody:not(.infoButton) {
  font-family: 'Roboto', sans-serif;
}
.v-avatar {
  height: 125px !important;
  width: 125px !important;
  overflow: visible !important;
}
.v-image {
  border-radius: 99px !important;
}
.v-image__image {
  background-position: 50% 2% !important;
}
.v-image__image,
.v-responsive__content {
  height: 125px !important;
  width: 125px !important;
}
.v-card__title,
.v-card__subtitle {
  text-align: left !important;
}
.v-card__title {
  line-height: 105% !important;
  padding-bottom: 01.2rem;
}
.v-card__subtitle {
  line-height: 110% !important;
}
.v-card {
  word-break: unset !important;
}
.buttonWrapper {
  margin-left: 0.5em;
}
.repButton {
  color: #8e8984 !important;
}
.repButton:hover {
  color: #363433 !important;
}
.repButton {
  font-size: 80%;
}
.spacer {
  min-height: 34px;
}

footer {
  display: block;
}

.headline {
  font-size: 20px !important;
}

.flex.pr-4.pt-0.mt-3.mb-0.pb-0.xs5.sm7.md7
  .v-responsive.v-image
  .v-image__image.v-image__image--cover {
  position: relative;
  border-radius: 50%;
  background-size: cover;
  background-repeat: no-repeat;
}

.layout.row {
  /* height: 160px; */
}
.sectionHeader:first-of-type {
  margin-top: 1em;
}
.sectionHeader {
  color: #343434;
  font-family: 'Roboto', sans-serif;
  border-bottom: 1px solid #d1cccc;
  text-align: left;
  /* position: relative; */
  font-size: 130%;
  padding-right: 2em;
  padding-left: 2em;
  font-weight: 400;
  letter-spacing: 0.08em;
  padding-bottom: 0.65em;
  margin-bottom: 0.3em !important;
}

h1,
h2 {
  font-weight: normal;
  color: black;
}

@media only screen and (min-width: 750px) {
  .v-responsive {
    right: 0.1em;
  }
}
@media only screen and (min-width: 600px) {
  .v-responsive.v-image {
    /* height: 115px;
    width: 115px; */
  }
  .v-btn.v-btn--icon.theme--light {
    margin-right: 0.1em;
  }
  .container.grid-list-lg .layout:only-child {
    margin: 0em;
  }
  .repName {
    font-size: 100%;
  }
  .repTitle {
    font-size: 80%;
  }
}
@media only screen and (min-width: 700px) and (max-width: 749px) {
  .v-responsive.v-image {
    right: -0.7em;
  }
}
@media screen and (min-width: 675px) and (max-width: 700px) {
  .v-responsive {
    /* top: -.4em; */
  }
}
@media screen and (min-width: 635px) and (max-width: 674px) {
  .v-responsive {
    /* top: -.6em; */
  }
}
@media screen and (min-width: 601px) and (max-width: 634px) {
  .v-responsive {
    /* top: -.9em; */
  }
}
@media only screen and (max-width: 599px) {
  .v-responsive.v-image {
    top: 0.3em;
    left: 0.5em;
    height: 155px;
    width: 155px;
  }
  .repTopText {
    position: relative;
    top: 0.5em;
    padding-left: 0px !important;
    left: -6px;
  }
  .v-card {
    margin: 0 auto;
    padding: 0 auto;
  }
  .v-btn.v-btn--icon.theme--light {
    position: relative !important;
    margin-top: 1em !important;
    margin-right: 0.2em !important;
    padding-bottom: 0px !important;
    margin-bottom: 0px !important;
  }
  .container.grid-list-lg .layout .flex {
    margin: 0 17px;
  }
}
@media screen and (max-width: 330px) {
  .v-responsive.v-image {
    left: -1.3em !important;
  }
  .repTitle {
    font-size: 95% !important;
  }
  .repName {
    font-size: 105% !important;
  }
  .sectionHeader {
    padding-right: 1em;
    padding-left: 1em;
  }
}
@media screen and (min-width: 350px) and (max-width: 380px) {
  .v-responsive.v-image {
    left: -0.6em !important;
  }
}
@media only screen and (max-width: 375px) {
  .container.grid-list-lg .layout .flex.cardWrapperFlex {
    margin: 0 auto;
  }
  .repButton {
    bottom: -0.5em;
    font-size: 90%;
  }

  .v-card__title {
    padding-top: 7px !important;
  }
  .v-card__actions {
    margin-top: 0px !important;
    height: 55px;
  }
  .v-responsive.v-image {
    height: 125px;
    width: 125px;
  }
}
@media screen and (min-width: 400px) and (max-width: 432) {
  .v-responsive.v-image {
    left: -0.2em !important;
  }
  .repTopText {
    top: 0em !important;
  }
  .v-card__title--primary {
    font-size: 110% !important;
  }
  .v-card__title {
    font-size: 105% !important;
  }
}
@media screen and (min-width: 350px) and (max-width: 432) {
  .repButton {
    bottom: -0.5em;
    font-size: 90%;
  }
  .v-card__title {
    padding-top: 7px !important;
  }
  .v-card__actions {
    margin-top: 0px !important;
    height: 55px;
  }
}
@media screen and (min-width: 350px) and (max-width: 500px) {
  .v-responsive.v-image {
    height: calc(155px - 5vw);
    width: calc(155px - 5vw);
  }
}
</style>
