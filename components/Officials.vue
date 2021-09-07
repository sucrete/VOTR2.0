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
                        {{ rep.addressLine0 }} <br />
                        <div v-if="rep.addressLine1">
                          {{ rep.addressLine1 }}
                        </div>
                        <!-- <br v-if="rep.addressLine1" /> -->
                        <!-- {{ rep.addressLine1 ? rep.addressLine1 :  }} <br /> -->
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
            'ocd-division/country:us': {
              name: 'United States',
              officeIndices: [0, 1],
            },
            'ocd-division/country:us/state:mo': {
              name: 'Missouri',
              officeIndices: [2, 4, 5, 6, 7, 8, 9, 10],
            },
            'ocd-division/country:us/state:mo/cd:5': {
              name: "Missouri's 5th congressional district",
              officeIndices: [3],
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
              name: 'Joseph R. Biden',
              address: [
                {
                  line1: '1600 Pennsylvania Avenue Northwest',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20500',
                },
              ],
              party: 'Democratic Party',
              phones: ['(202) 456-1111'],
              urls: ['https://www.whitehouse.gov/'],
              photoUrl:
                'https://smhttp-ssl-58547.nexcesscdn.net/nycss/images/uploads/candidates/_cropped350-420/JoeBiden21.jpg',
              channels: [
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
              name: 'Kamala Harris',
              address: [
                {
                  line1: '1600 Pennsylvania Avenue Northwest',
                  city: 'Washington',
                  state: 'DC',
                  zip: '20500',
                },
              ],
              party: 'Democratic Party',
              phones: ['(202) 456-1111'],
              urls: ['https://www.whitehouse.gov/'],
              photoUrl:
                'https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Senator_Harris_official_senate_portrait.jpg/450px-Senator_Harris_official_senate_portrait.jpg',
              channels: [
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
              photoUrl:
                'https://seawaves.com/wp-content/uploads/Hawley_Official_Portrait_400x.jpg',
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
                'https://pbs.twimg.com/profile_images/1349377305517432833/VSFz5pZB_400x400.jpg',
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
              photoUrl:
                'https://dehayf5mhw1h7.cloudfront.net/wp-content/uploads/sites/1028/2019/09/24092635/lt-gov-mike-kehoe.jpg',
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
              photoUrl:
                'https://www.sos.mo.gov/CMSImages/SOSMain/BioPortrait.jpg',
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
              photoUrl:
                'https://pbs.twimg.com/profile_images/1366423906014257153/0cdbg0Rv_400x400.jpg',
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
              photoUrl:
                'data:image/jpeg;base64,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',
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
              photoUrl:
                'https://bloximages.chicago2.vip.townnews.com/stlamerican.com/content/tncms/assets/v3/editorial/7/c5/7c5d8740-db4c-11e9-8163-076fcef4f299/5d84369e13756.image.jpg?crop=989%2C949%2C101%2C92',
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
            },
            {
              name: 'Patricia Breckenridge',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
              photoUrl:
                'https://yourmissourijudges.org/wp-content/uploads/2014/01/breckenridge.jpg',
            },
            {
              name: 'Paul C. Wilson',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
              photoUrl: 'https://www.courts.mo.gov/image.jsp?id=59002',
            },
            {
              name: 'Zel M. Fischer',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
              photoUrl: 'https://www.courts.mo.gov/image.jsp?id=46822',
            },
            {
              name: 'Laura Denvir Stith',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
              photoUrl: 'https://www.courts.mo.gov/image.jsp?id=70193',
            },
            {
              name: 'Mary R. Russell',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
              photoUrl:
                'http://yourmissourijudges.org/wp-content/uploads/2018/09/Mary-Russell-Photo-684x1030.jpg',
            },
            {
              name: 'W. Brent Powell',
              party: 'Nonpartisan',
              phones: ['(573) 751-4144'],
              urls: ['https://www.courts.mo.gov/page.jsp?id=27'],
              photoUrl: 'https://www.courts.mo.gov/image.jsp?id=113630',
            },
            {
              name: 'Nicole Galloway',
              party: 'Democratic Party',
              phones: ['(800) 347-8597'],
              urls: ['https://auditor.mo.gov/'],
              emails: ['moaudit@auditor.mo.gov'],
              photoUrl:
                'https://www.koamnewsnow.com/content/uploads/2020/10/Galloway-Nicole.png',
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
              photoUrl:
                'https://www.jacksoncountysheriff.org/files/assets/sheriff/about-us/images/darrylforte.jpeg?dimension=pageimage&w=480',
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
              photoUrl:
                'https://greatermo.org/wp-content/uploads/2018/04/Jean-Peters-Baker-Portrait-8-e1554078373622-225x300.jpg',
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
              photoUrl:
                'https://www.jacksongov.org/files/sharedassets/public/our-county/images/elected-officials/frank_white2.jpg?dimension=pageimage&w=480',
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
              photoUrl:
                'https://media-exp1.licdn.com/dms/image/C4E03AQHiV_1CusYeIg/profile-displayphoto-shrink_800_800/0/1516800664051?e=1636588800&v=beta&t=9uH84sYCDVTa0tH1Y-XT_ym3i2c2NL00DX1LCzGI_Gk',
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
              photoUrl:
                'http://p3cdn4static.sharpschool.com/UserFiles/Servers/Server_133223/Image/Miller_032_150908-Edit-2.JPG',
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
              photoUrl:
                'https://www.jacksongov.org/files/sharedassets/public/our-county/images/elected-officials/janderson.jpg?w=600',
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
                  'https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Joe_Biden_official_portrait_2013_cropped.jpg/383px-Joe_Biden_official_portrait_2013_cropped.jpg'
              } else if (corazon === 1) {
                officialObject1.repPhotoURL =
                  'https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Senator_Harris_official_senate_portrait.jpg/450px-Senator_Harris_official_senate_portrait.jpg'
              }
              const theOfficial = GState.data.officials[corazon]
              officialObject1.party = theOfficial.party
              if (theOfficial.address !== undefined) {
                const _oa = theOfficial.address[0]
                officialObject1.addressLine0 = _oa.line1
                officialObject1.addressLine1 = _oa.line2 || null
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
  word-break: unset;
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
