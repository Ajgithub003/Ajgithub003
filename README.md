import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Create figure and axes
fig, ax = plt.subplots(figsize=(14, 12))

# Function to draw a box with text
def draw_box(ax, text, xy, width=2, height=1, boxstyle='round,pad=0.3', boxcolor='lightgrey', textcolor='black'):
    box = patches.FancyBboxPatch(xy, width=width, height=height, boxstyle=boxstyle, color=boxcolor)
    ax.add_patch(box)
    cx = xy[0] + width / 2.0
    cy = xy[1] + height / 2.0
    ax.annotate(text, (cx, cy), color=textcolor, weight='bold', fontsize=10, ha='center', va='center')

# Function to draw an arrow
def draw_arrow(ax, start, end):
    ax.annotate('', xy=end, xytext=start, arrowprops=dict(arrowstyle="->", lw=1.5))

# Disable axes
ax.set_axis_off()

# Define positions
positions = {
    'start': (5, 20),
    'registration': (5, 18),
    'doc_upload': (5, 16),
    'select_lender': (5, 14),
    'loan_application': (5, 12),
    'lender_notification': (5, 10),
    'background_check': (5, 8),
    'approval': (3, 6),
    'rejection': (7, 6),
    'agreement': (3, 4),
    'disbursement': (3, 2),
    'repayment_schedule': (5, 4),
    'monthly_repayment': (5, 2),
    'transaction_monitoring': (8, 8),
    'reporting': (8, 6),
    'support': (8, 2),
}

# Draw boxes
draw_box(ax, "Start", positions['start'], boxcolor='lightblue')
draw_box(ax, "User Registration", positions['registration'])
draw_box(ax, "Document Upload", positions['doc_upload'])
draw_box(ax, "Select Money Lender (State-wise)", positions['select_lender'])
draw_box(ax, "Loan Application", positions['loan_application'])
draw_box(ax, "Lender Notification", positions['lender_notification'])
draw_box(ax, "Background Check", positions['background_check'])
draw_box(ax, "Approval", positions['approval'], boxcolor='lightgreen')
draw_box(ax, "Rejection", positions['rejection'], boxcolor='lightcoral')
draw_box(ax, "Loan Agreement", positions['agreement'])
draw_box(ax, "Disbursement", positions['disbursement'])
draw_box(ax, "Repayment Schedule", positions['repayment_schedule'])
draw_box(ax, "Monthly Repayment", positions['monthly_repayment'])
draw_box(ax, "Transaction Monitoring", positions['transaction_monitoring'], boxcolor='lightyellow')
draw_box(ax, "Reporting", positions['reporting'], boxcolor='lightyellow')
draw_box(ax, "Customer Support", positions['support'], boxcolor='lightgrey')

# Draw arrows
draw_arrow(ax, positions['start'], positions['registration'])
draw_arrow(ax, positions['registration'], positions['doc_upload'])
draw_arrow(ax, positions['doc_upload'], positions['select_lender'])
draw_arrow(ax, positions['select_lender'], positions['loan_application'])
draw_arrow(ax, positions['loan_application'], positions['lender_notification'])
draw_arrow(ax, positions['lender_notification'], positions['background_check'])
draw_arrow(ax, positions['background_check'], positions['approval'])
draw_arrow(ax, positions['background_check'], positions['rejection'])
draw_arrow(ax, positions['approval'], positions['agreement'])
draw_arrow(ax, positions['agreement'], positions['disbursement'])
draw_arrow(ax, positions['disbursement'], positions['monthly_repayment'])
draw_arrow(ax, positions['monthly_repayment'], positions['repayment_schedule'])
draw_arrow(ax, positions['transaction_monitoring'], positions['reporting'])

# Draw horizontal arrows for KPKT oversight and support
draw_arrow(ax, (8, 5), (8, 3))
draw_arrow(ax, (5, 1), (8, 1))

plt.title("Money Lending App Flowchart for Malaysia")
plt.show()
