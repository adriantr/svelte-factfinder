<script>
  function handleClick(e) {
    alert("Clicked");
  }

  import FF from './ff.svelte'
</script>

<FF/>
<nav class="flex items-center p-6 bg-transparent relative mx-auto">
  <img
    class="h-6 w-16 cursor-pointer"
    src="https://upload.wikimedia.org/wikipedia/commons/4/42/Elkjop_logo_blue.png"
    on:click={handleClick} />
  <div class="flex justify-center w-5/6">
    <ff-searchbox class="w-1/2">
      <input
        class="border-2 border-gray-300 bg-white h-10 px-5 pr-16 rounded-lg
          text-sm focus:outline-none w-full"/>
    </ff-searchbox>
  </div>
</nav>

<div class="flex">
  <ff-asn class="w-1/5">
    <ff-asn-group filter-style="TREE" />

    <!-- Acts as a template for all MULTISELECT configured filter groups -->
    <ff-asn-group filter-style="MULTISELECT" />

    <ff-asn-group filter-style="DEFAULT">
      <div data-container="detailedLinks">
        <div data-content="detailedLinks">
          <!-- always visible items will be added here -->
        </div>
      </div>
      <div data-container="showMore">
        <!-- The "showMore" container will only be rendered if there are "hiddenLinks" in the FACT-Finder response.
                     It disappears after being clicked and reappears after "showLess" was clicked. -->
        <span class="text">Show More</span>
      </div>

      <!-- The "hiddenLinks" and "showLess" containers are only rendered after "showMore" was clicked.
                 They disappear after "showLess" was clicked. -->

      <div data-container="hiddenLinks">
        <div data-content="hiddenLinks">
          <!-- hidden items will be added here -->
        </div>
      </div>
      <div data-container="showLess"><span class="text">Show Less</span></div>
    </ff-asn-group>
  </ff-asn>

  <div>
      <div class="flex justify-center p-8">
        <span>You've searched for:
          <ff-breadcrumb-trail /></span>
      </div>

    <ff-record-list class="w-4/5">
      <div
        class="grid xl:grid-cols-3 lg:grid-cols-2 md:grid-cols-2 sm:grid-cols-1
          xs:grid-cols-1 gap-2">
        <ff-record disable-overwrite>
          <div
            class="card flex flex-col justify-center p-10 bg-white rounded-lg
              shadow-2xl">
            <div class="prod-title">
              <p id="name" class="text-2xl uppercase text-gray-900 font-bold truncate">
                [[record.Name]]
              </p>
              <p class="uppercase text-sm text-gray-400">
                [[record.AltArticleNumber]]
              </p>
            </div>
            <div class="prod-img flex justify-center">
              <img
                src="[[record.Image]]"
                class="object-scale-down h-48 object-center" />
            </div>
            <div class="prod-info grid gap-10">
              <div
                class="flex flex-col md:flex-row justify-between items-center
                  text-gray-900">
                <button
                  onclick="handleClick(event)"
                  class="px-6 py-2 transition ease-in duration-200 uppercase
                    rounded-full hover:bg-gray-800 hover:text-white border-2
                    border-gray-900 focus:outline-none">Add to cart</button>

                <p id="price" class="font-bold text-xl">[[record.MasterChainPrice]],-</p>
              </div>
            </div>
          </div>
        </ff-record>
      </div>
    </ff-record-list>
  </div>
</div>
