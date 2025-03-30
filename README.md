# demograpyx

A set of asynchronous bindings for the three Demograpix APIs: [`genderize`](https://genderize.io/), [`agify`](https://agify.io) and [`nationalize`](https://nationalize.io)

## Example usage

Functions are identical across all three API clients (`predict`, `batch_predict`)

```py
import asyncio
from demograpyx import Genderize, CountryCode

async def main() -> None:
    genderize = await Genderize.create() # optionally pass api_key kwarg for API key
    # alternatively, initialise an aiohttp.ClientSession and pass it as a kwarg
    # genderize = Genderize(session=aiohttp.ClientSession())

    data = await genderize.predict("Mike", country_id=CountryCode.UnitedStates)
    print(f"{data.gender} - {data.probability}")
    # "male - 1.0"

if __name__ == "__main__":
    asyncio.run(main())
```