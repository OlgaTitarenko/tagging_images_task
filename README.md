# Annotating Images
## Objective: 
Create an interface, which allows the user to tag full images or parts of an image using a tag hierarchy with two levels. Send updates to the store over a WebSockets channel as a side-effect using [https://redux-observable.js.org](https://redux-observable.js.org)

## Scenario:
1. User is presented with a list (or grid) view of tagged images (get a list of images on [https://unsplash.com/search/photos/market](https://unsplash.com/search/photos/market)), as well as an input field, which provides filtering by tag.
2. User selects an image from the list and is presented with a tagging interface which must include the image itself, as well as a hierarchical tag list with two levels.
3. User can tag the whole image area by clicking on a tag in the list.
4. User can tag a rectangular part of the image by dragging a tag from the list and dropping it on the image. The tagged area should be centered around the coordinates where the tag was dropped, but not extend beyond the bounds of the image.
5. User can resize the tagged area after tagging an image.
6. User can add multiple tags to an image
7. Tags can be removed by clicking on an active tag in the list. User must be able to undo this operation and get an already removed tag back.
8. Tags can be rearranged within the bounds of an image.
9. After saving, user is taken back to the list/grid view which is updated with the new data and can filter images by tag using the input field

## Things to keep in mind:
- Images can be scaled down after tagging. Tag coordinates should remain valid.
- Activating a second-level tag (e.g. People/Customer) should imply that the top-level tag (People) is active as well.
- Deactivating a first-level tag should deactivate second-level tags.
- The list of tags is fixed, no need to add new tags.
- Second-level tags should be presented in the form:   
	"First-level Tag/Second-level Tag"
- Separate concerns using presentational and container components
- Use immutable data structures

## TODO:
- [ ] Develop appropriate JSON data structures for images, tags and associations.
- [ ] Create needed views, components, stores implementing the described functions.
- [ ] Bonus: send/receive updates to the Redux Store over a WebSocket connection using redux-observable epic so that two users can tag the same images together.

## Example of a tag structure
People

↳Artisan

↳ Customer

↳ Vendor

↳ Passerby

↳ Waiter

Food

↳ Bread

↳ Cheese

↳ Fish

↳ Fruit

↳ Honey

↳ Meat

↳ Noodles

↳ Snacks

↳ Spices

↳ Vegetable

Drinks

↳ Alcohol

↳ Milk

↳ Soft-drink

Non-Food

↳ Books

↳ Clothes

↳ Electronics

↳ Flowers

↳ Hand-made Objects

↳ Jewelry

↳ Shoes

↳ Souvenirs

↳ Tools

Signage

↳ Ad

↳ Brand

↳ Graffiti

↳ House

↳ Marquee

↳ Note

↳ Price

↳ Street Sign

Containers

↳ Basket

↳ Bag

↳ Box

Structures

↳ Cafe

↳ Lot

↳ Restaurant

↳ Stand

↳ Stall

Africa

Asia

↳ China

↳ India

↳ Middle East

↳ Southeast Asia

Europe

↳ East Europe

↳ West Europe

North America

↳ Canada

↳ USA

South America

↳ Carribbean

↳ Latin America

Oceania

↳ Australia

↳ New Zealand

↳ Pacific Islands
