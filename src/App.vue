<template>
    <nav class="navbar is-transparent" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
            <div class="navbar-burger" data-target="navbarExampleTransparentExample">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>

        <div id="navbarBasicExample" class="navbar-menu">
            <div class="navbar-start">
            </div>

            <div class="navbar-end">
                <a class="navbar-item" @click="section='team'" :class="{'is-active':(section === 'team')}">
                    Team
                </a>

                <a class="navbar-item" @click="section='portfolio'" :class="{'is-active':(section === 'portfolio')}">
                    Portfolio
                </a>

                <a class="navbar-item" @click="section='services'" :class="{'is-active':(section === 'services')}">
                    Services
                </a>

                <div class="navbar-item">
                    <div class="buttons">
                        <a class="button is-primary" href="mailto:info@scarce.art">Contact Us</a>
                    </div>
                </div>
            </div>
        </div>
    </nav>
    <div class="columns is-pulled-up main-columns">
        <div class="column is-6 has-text-right has-background-black">
            <h1 class="title proxima has-text-white is-pushed-down">SCARCE</h1>

            <section class="section" v-if="section === 'team'">
                <h2 class="title has-text-primary">Team</h2>
                <div class="tabs is-right">
                    <ul>
                        <li :class="{'is-active':(selected === 'shaun')}"><a @click="selected='shaun'">Shaun</a></li>
                        <li :class="{'is-active':(selected === 'sara')}"><a @click="selected='sara'">Sara</a></li>
                        <li :class="{'is-active':(selected === 'mark')}"><a @click="selected='mark'">Mark</a></li>
                    </ul>
                </div>

                <div class="columns">
                    <div class="column"></div>

                    <div class="column is-6">
                        <div class="card">
                            <div class="card-image">
                                <figure class="image is-square">
                                    <img :src="team[selected].image">
                                </figure>
                            </div>

                            <div class="card-content">
                                <div class="media">
                                    <div class="media-content">
                                        <p class="title is-4">{{team[selected].name}}</p>
                                        <p class="subtitle is-6"><a :href="'https://twitter.com/' + team[selected].twitter" target="_blank">@{{team[selected].twitter}}</a></p>
                                    </div>
                                </div>

                                <div class="content">
                                    {{team[selected].description}}
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section class="section" v-if="section === 'portfolio'">
                <h2 class="title has-text-primary">Portfolio</h2>
                <div class="tabs is-right">
                    <ul>
                        <li :class="{'is-active':(selectedPortfolio === 'stonersrock')}"><a @click="selectedPortfolio='stonersrock'">Stoners Rock</a></li>
                        <li :class="{'is-active':(selectedPortfolio === 'bingoswap')}"><a @click="selectedPortfolio='bingoswap'">Bingo Swap</a></li>
                        <li :class="{'is-active':(selectedPortfolio === 'halloweeners')}"><a @click="selectedPortfolio='halloweeners'">Halloweeners</a></li>
                    </ul>
                </div>

                <div class="columns">
                    <div class="column"></div>

                    <div class="column is-6">
                        <div class="card">
                            <div class="card-image">
                                <figure class="image is-square">
                                    <img :src="portfolio[selectedPortfolio].image">
                                </figure>
                            </div>

                            <div class="card-content">
                                <div class="media">
                                    <div class="media-content">
                                        <p class="title is-4">{{portfolio[selectedPortfolio].name}}</p>
                                        <p class="subtitle is-6"><a :href="'https://twitter.com/' + portfolio[selectedPortfolio].twitter" target="_blank">@{{portfolio[selectedPortfolio].twitter}}</a></p>
                                    </div>
                                </div>

                                <div class="content">
                                    {{portfolio[selectedPortfolio].description}}<br />
                                    <a :href="portfolio[selectedPortfolio].link" target="_blank">{{portfolio[selectedPortfolio].link}}</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section class="section" v-if="section === 'services'">
                <h2 class="title">Services</h2>
                Coming Soon
            </section>

        </div>
        <div class="column is-6 has-text-left">

            <h1 class="title proxima has-text-black">ART</h1>

            <section class="section" v-if="section === 'team'">
                <h2 class="title">{{selected}}'s NFTs</h2>
                <div class="columns is-multiline is-nfts">
                    <div class="column is-3" v-for="nft in team[selected].nfts" :key="nft.id">
                        <figure class="image is-square">
                            <img :src="nft.image_url" />
                        </figure>
                    </div>
                </div>
            </section>

            <section class="section" v-if="section === 'portfolio'">
                <h2 class="title">{{portfolio[selectedPortfolio].name}}'s NFTs</h2>
                <div class="columns is-multiline is-nfts">
                    <div class="column" v-if="portfolio[selectedPortfolio].nfts.length === 0">
                        <p>Project NFTs coming soon.</p>
                    </div>
                    <div class="column is-3" v-for="nft in portfolio[selectedPortfolio].nfts" :key="nft.id">
                        <figure class="image is-square">
                            <img :src="nft.image_url" />
                        </figure>
                    </div>
                </div>
            </section>

        </div>
    </div>
</template>

<script>

export default {
  name: 'App',
  components: {

  },
  data: function() {
    return {
      section: 'team',
      selected: 'shaun',
      selectedPortfolio: 'stonersrock',
      team: {
        shaun: {
          name: 'Shaun',
          twitter: 'sircryptos',
          description: 'Entrepreneur turned NFT collector trying to bring love to NFTs! BAYC, Alien boys, BOTB and HOK owner.',
          image: "/sircryptos.jpg",
          wallet: '0xa809e097f1ec8ecc8d2677d70c2f32742851dd62',
          nfts: [],
        },
        sara: {
          name: 'Sara',
          twitter: 'altcryp',
          description: 'Shadowy Super Coder. I play VR and vape a lot. I also code smart contracts for fun.',
          image: "/altcryp.png",
          wallet: '0x00796e910Bd0228ddF4cd79e3f353871a61C351C',
          nfts: [],
        },
        mark: {
          name: 'Mark',
          twitter: 'linedetail',
          description: 'I\'m an artist and animator, and I made a badass deck of cards.',
          image: "/linedetail.jpg",
          wallet: '0xB58Fb5372e9Aa0C86c3B281179c05Af3bB7a181b',
          nfts: []
        }
      },
      portfolio: {
        stonersrock: {
          name: 'Stoners Rock',
          twitter: 'mystoners',
          description: '10,420 pet rocks minted on the Ethereum blockchain.',
          image: "/rock.png",
          collection: '0x13df7973ea203868af66fcffd86fe8cb63edd378',
          nfts: [],
          link: 'https://stonersrock.com'
        },
        bingoswap: {
          name: 'Bingo Swap',
          twitter: 'nftbingo',
          description: 'Play BINGO on the Blockchain with verifiable randomness and ETH prizes.',
          image: "/bingo.png",
          collection: '',
          nfts: [],
          link: 'https://bingoswap.art'
        },
        halloweeners: {
          name: 'Halloweeners',
          twitter: 'halloweeners',
          description: '6,666 Halloween themed avatars minted on the Ethereum blockchain.',
          image: "/halloweeners.gif",
          collection: '',
          nfts: [],
          link: 'https://halloweeners.art'
        }

      }

    }
  },
  mounted: function() {
    this.getNFTs();
  },
  methods: {
    getNFTs: async function() {
        let apiUrl = 'https://api.opensea.io/api/v1/assets?limit=50&owner=' + this.team.shaun.wallet;
        let response = await fetch(apiUrl);
        let data = await response.json();
        this.team.shaun.nfts = data.assets;

        apiUrl = 'https://api.opensea.io/api/v1/assets?limit=50&owner=' + this.team.sara.wallet;
        response = await fetch(apiUrl);
        data = await response.json();
        this.team.sara.nfts = data.assets;

        apiUrl = 'https://api.opensea.io/api/v1/assets?limit=50&owner=' + this.team.mark.wallet;
        response = await fetch(apiUrl);
        data = await response.json();
        this.team.mark.nfts = data.assets;

        apiUrl = 'https://api.opensea.io/api/v1/assets?asset_contract_address=' + this.portfolio.stonersrock.collection + '&order_direction=desc&offset=0&limit=50';
        response = await fetch(apiUrl);
        data = await response.json();
        console.log('data', data);
        this.portfolio.stonersrock.nfts = data.assets;
    }
  }
}
</script>

<style>
    html, body, #app {
        height: 100%;
    }
    .title {
        text-transform: uppercase;
        font-weight: 900;
    }
    .main-columns {
        min-height: 100%;
    }
    .proxima {
        font-weight: 900 !important;
        font-size: 7em !important;
    }
    .card-wrapper {
        width: 500px;
    }
    .tabs ul {
        border-bottom: 0;
    }
    .pull-right {
        float: right;
        margin: 1em;
    }
    .is-pulled-up {
        margin-top: -65px;
    }
    .navbar {
        background: transparent !important;
    }
    a.navbar-item.is-active {
        text-decoration: underline;
    }
    .is-nfts {
        margin-top: 4.5em;
    }
</style>
