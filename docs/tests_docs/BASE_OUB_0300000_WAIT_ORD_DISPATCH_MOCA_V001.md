# **BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001**


<!-- SMART_DOC_GEN_TEST_DESCR - Start -->
This test builds on other BASE outbound tests.  The test will wait for the outbound order to be completely dispatched.
<!-- SMART_DOC_GEN_TEST_DESCR - End -->

## **Test Category**

**☐** Custom  
**☐** Smart IS  
**🗹** Standard  

## **Overview**

In the described use case, the system is designed to wait for an order to be dispatched, indicating a process that involves monitoring the status of an order until it reaches the "dispatched" state. This likely involves a system that tracks orders and their statuses, possibly interfacing with other systems or components that handle the actual dispatching process. The waiting mechanism may involve periodic checks of the order status or subscribing to notifications or events that indicate when an order has been dispatched. This functionality is crucial for ensuring that downstream processes or actions dependent on the order being dispatched are triggered at the right time.

To implement this use case effectively, the system needs to have a robust mechanism for tracking and managing order statuses. It should be able to handle various scenarios, such as delays or errors in the dispatch process, and provide visibility into the status of each order.

## **Applicable versions**

This test is designed to support versions greater than **2008.x.x**,
ensuring compatibility and smooth operation with the latest software
releases. Users can confidently utilize this test, as it is optimized
for newer versions while retaining a user-friendly testing process.

## **Test Arguments**

Test arguments are parameters or inputs that are passed to the test
cases to customize the test execution. These arguments provide
flexibility and allow for the reuse of the same test case with different
sets of data or configurations. The input is as follows:


<!-- SMART_DOC_GEN_TEST_ARG - Start -->
<table>
<tr><th>Arguments</th><th>Argument Description</th></tr>
<tr><td>ordnum</td><td>Order number.</td></tr>
<tr><td>schbat</td><td>This parameter specifies the schbat to create. If it is not passed, the uc_schbat_expr expression is used to determine its value.</td></tr>
<tr><td>ship_id</td><td>Can pass in an explicit ship_id if needed.</td></tr>
<tr><td>uc_max_iter</td><td>To avoid an infinite loop, we cap the number of iterations. The default is 1000.</td></tr>
<tr><td>uc_sleep_ms_each_iter</td><td>It provides a pattern for load numbers to move.</td></tr>
<tr><td>uc_test_exec_seqnum</td><td>During each run, it generates a unique base-36 value.</td></tr>
<tr><td>uc_wave_set_expr</td><td>To locate data for the test run, set a default wave set. Default is as we used during order creation, i.e., "AW" || @uc_test_exec_seqnum.</td></tr>
<tr><td>wave_set</td><td>You can explicitly pass in a wave set for specific cases.</td></tr>
<tr><td>wh_id</td><td>This refers to the warehouse ID.</td></tr>
</table>
<!-- SMART_DOC_GEN_TEST_ARG - End -->

## **TestCases using this test**

This section provides a comprehensive list of test cases that are associated with this particular test. It provides a quick reference for understanding the specific tests covered. By reviewing these test cases, users can gain a deeper understanding of how this test is used in different scenarios and ensure comprehensive test coverage.


<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - Start -->
| Test Case ID | Test Case Description |
| ------------ | --------------------- |
| BASE_ALL_GEN | null |

<!-- SMART_DOC_GEN_TEST_CASE_USING_THIS - End -->

## **RunSets using this test**

This section details the various RunSets that utilize this test as part of their execution. Each RunSet represents a collection of tests and configurations that are executed together to achieve specific testing goals. By examining the RunSets that include this test, users can understand how it fits into larger testing scenarios and how it contributes to overall test coverage and automation.


<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - Start -->
| Run Set ID | Run Set Description |
| ---------- | ------------------- |
| BASE_OUB_000000_CREATE_TO_DISPATCH | create order, plan, allocate, release, pick, dispatch |
| BASE_OUB_000000_CREATE_TO_DISPATCH | create order, plan, allocate, release, pick, dispatch |
| BASE_OUB_000100_CREATE_TO_DISPATCH_USING_FRONT_END | create order, plan, allocate (web), release, pick, dispatch |

<!-- SMART_DOC_GEN_RUN_SET_USING_THIS - End -->

## **Equivalent Usecase**

The following steps represent a general procedure for dispatched order through GUI.

**Step:1**

Select **Configuration** > **Outbound Planner**

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001.png)

**Step:2**

Click on the **'Wave and Pick'** screen.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image2.png)

**Step:3**

From the **Actions** drop-down list, select **Plan Wave.**

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image3.png)

**Step:4**

Under **Search Criteria**, from the **Rule Name** drop-down list, select the rule that defines the parameters by which to search for orders or shipments. Click **Search**. The orders or shipments that meet the search criteria are displayed.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image4.png)

**Step:5**

Click **Plan Wave.**

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image5.png)

**Step:6**

Open that Plan wave and go to the '**Actions**' tab and pick '**Allocate Wave (Planned)**'.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image6.png)

**Note**: Picks in a specific LPN level are released whenever the check box for the LPN level is selected for immediate release or when all three LPN levels are deselected.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image7.png)

**Step:7**

After that, you need to confirm pick and add load

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image8.png)

**Step:8**

After that, you need to add equipment and attach that equipment to the specified load.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image9.png)

**Step:9**

After that, you need to go to **receiving** and **door activity** and select your equipment.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image10.png)

**Step:10**

Select your equipment and go to action.

![](BASE_OUB_0300000_WAIT_ORD_DISPATCH_MOCA_V001/image11.png)

## **Applicable MOCA commands**

To dispatch order using the MOCA command, you can use the following command.

- ord dispatched

This command will trigger the dispatch order based on the predefined parameters and rules within the MOCA system.

## **Affected DB tables**

The following database table is typically affected while dispatching the order:

- **Order**
- **Shipment**
- **Shipment_line**

These tables are likely to be affected to ensure proper tracking and management of the dispatch process and associated shipments.

---

**Previous-Test**
 [BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001](./tests_docs/BASE_OUB_0080A00_SMART_PALBLD_MOCA_V001.md)
 
**Next-Test**
  [BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001](./tests_docs/BASE_OUB_0010000_ORD_COPY_TEMPLATE_MOCA_V001.md)
  
[SMART-IS](https://www.smart-is.pk) 